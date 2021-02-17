---


---

<h2 id="volume-assignment-in-real-world-story">Volume Assignment in real world story:</h2>
<p>To install postgres database volume with different version but in the same path of volume:</p>
<p>Old version:</p>
<ul>
<li><code>docker container run -d --name psql -v psql:/var/lib/postgresql/data -e POSTGRES_PASSWORD=123456 postgres:9.6.19</code><br>
<ins>Note</ins>: From Docker Hub, find the volume path <code>/var/lib/postgresql/data</code></li>
<li><code>docker container logs -f psql</code> to check installation status</li>
</ul>
<p>Latest version:</p>
<ul>
<li><code>docker container run -d --name psql2 -v psql:/var/lib/postgresql/data -e POSTGRES_PASSWORD=123456 postgres:13.0</code></li>
<li><code>docker container logs -f psql</code> to check installation status</li>
</ul>
<h2 id="bind-mounting-assignment">Bind Mounting Assignment:</h2>
<p>use a Jekyll “Static Site Generator” to start a local web server using <a href="https://www.github.com/BretFisher/udemy-docker-mastery/tree/main/bindmount-sample-1/">bindmount-sample-1</a> template.<br>
Inside the template directory:</p>
<ul>
<li><code>docker container run -p 3307:4000 -v $(pwd):/site bretfisher/jekyll-serve</code> that will map jekyll-serve website to container - bretfisher/jekyll-serve and served on port localhost:3307.</li>
<li>Go change file inside of  <code>_posts</code> folder, this automatically updated the website.</li>
</ul>
<p><a href="https://docs.docker.com/compose/">Docker Compose File Template</a>:</p>
<pre><code>version: '3.1'  # if no version is specified then v1 is assumed. Recommend v2 minimum
    services: # containers. same as docker run
	    servicename: # a friendly name. this is also DNS name inside network
		    image: # Optional if you use build:
		    command: # Optional, replace the default CMD specified by the image
		    environment: # Optional, same as -e in docker run
		    volumes: # Optional, same as -v in docker run
		servicename2:
	volumes: # Optional, same as docker volume create
	networks: # Optional, same as docker network create
</code></pre>
<h2 id="multi-container-service-assignment">Multi-Container Service Assignment:</h2>
<ul>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="true" disabled=""> Build a basic compose file for Drupal content management system website</li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="true" disabled=""> Drupal image with postgres image</li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="true" disabled=""> Ports 8080</li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="true" disabled=""> Set <code>POSTGRES_PASSWORD</code> for postgres</li>
</ul>
<h3 id="installation-notes">Installation Notes:</h3>
<p><code>docker-compose up</code>: <a href="https://www.linode.com/docs/guides/drupal-with-docker-compose/">offical doc</a></p>
<pre><code>version: '3.8'
services:
	  drupal:
		  image: drupal
		  ports:
			  - "8080:80"
		  volumes:
			  - drupal-modules:/var/www/html/modules
			  - drupal-profiles:/var/www/html/profiles
			  - drupal-sites:/var/www/html/sites
			  - drupal-themes:/var/www/html/themes
		  restart: always
	  postgres:
		  image: postgres
		  environment:
			  - POSTGRES_PASSWORD=123456
		  volumes:
			  - drupal-data:/var/lib/postgresql/data
		  restart: always
volumes:
    drupal-data:
    drupal-modules:
	drupal-profiles:
	drupal-sites:
    drupal-themes:
</code></pre>
<h3 id="debug-logs">Debug logs:</h3>
<h4 id="bugs">bugs:</h4>
<pre><code>postgres_1  | 2020-11-08 02:52:54.576 UTC [32] FATAL:  password authentication failed for user "postgres"
postgres_1  | 2020-11-08 02:52:54.576 UTC [32] DETAIL:  Password does not match for user "postgres".
</code></pre>
<h4 id="solution">solution:</h4>
<p>Navigate to postgresql shell:<br>
<code>docker container exec -it compose-assignment-1_postgres_1 psql -U postgres</code><br>
Alter password:<br>
<code>postgres=# ALTER ROLE postgres WITH PASSWORD '666666';</code><br>
Quit postgresql and done:<br>
<code>postgres=# \q</code></p>
<h3 id="setup-drupal-cms-web-localhost8080">Setup Drupal CMS Web: <a href="http://localhost:8080/">localhost:8080</a></h3>
<p>See offical document: <a href="https://www.linode.com/docs/guides/drupal-with-docker-compose/">Install Drupal with docker compose file</a></p>
<h3 id="adding-custom-image-to-compose-files">Adding Custom Image to Compose Files:</h3>
<p><a href="https://github.com/BretFisher/udemy-docker-mastery/tree/main/compose-sample-3">Reference</a></p>
<p>docker-compose file:</p>
<pre><code>version: '3.8'
services:
	proxy:
		build:
			context: .
			dockerfile: nginx.Dockerfile
		ports:
			- '80:80'
	web:
		image: httpd
		volumes:
			- ./html:/usr/local/apache2/htdocs
</code></pre>
<p>Note: docker will build custom image based on <code>dockerfile: nginx.Dockerfile</code> and  the name of custom image is default <code>directory_name_proxy</code> and <code>directory_name_web</code></p>
<p>Get into docker-compose root directory:<br>
<code>docker-compose up</code> or <code>docker-compose up -d</code><br>
Note: To rebuild this image you must use <code>docker-compose build</code> or <code>docker-compose up --build</code></p>
<h3 id="clean-up">Clean up:</h3>
<p><code>docker-compose down -v</code> to stop container and remove volumes;<br>
<code>docker-compose down --rmi</code> to stop container and remove local image that does not have custom tag in it.</p>
<h2 id="run-time-image-building-and-multi-container-assignment">Run-Time Image Building and Multi-Container Assignment</h2>
<ul>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" disabled=""> Build custom Drupal image for local testing</li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" disabled=""> Make Dockerfile and docker-compose.yml in dir <a href="https://github.com/BretFisher/udemy-docker-mastery/tree/main/compose-assignment-2">compose-sample-assignment-2</a></li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" disabled=""> Use the drupal image along with the postgres image as before</li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" disabled=""> Use <a href="https://github.com/BretFisher/udemy-docker-mastery/tree/main/compose-assignment-2">README.md</a> for detail</li>
</ul>
<h3 id="installation-notes-1">Installation Notes:</h3>
<p><a href="https://github.com/BretFisher/udemy-docker-mastery/blob/main/compose-assignment-2/answer/docker-compose.yml">docker-compose.yml</a><br>
<a href="https://github.com/BretFisher/udemy-docker-mastery/blob/main/compose-assignment-2/answer/Dockerfile">Dockerfile</a></p>
<h3 id="setup-drupal-cms-web-localhost8080-1">Setup Drupal CMS Web: <a href="http://localhost:8080/">localhost:8080</a></h3>
<p>See offical document: <a href="https://www.linode.com/docs/guides/drupal-with-docker-compose/">Install Drupal with docker compose file</a><br>
Addition: Setup Appearance -&gt; install bootstrap template</p>
<h3 id="cleanup">Cleanup:</h3>
<p><code>docker-compose down</code></p>
<h2 id="multi-service-multi-node-web-app">Multi-Service Multi-Node Web App</h2>
<h3 id="installation-note-instructions">Installation Note: <a href="https://github.com/BretFisher/udemy-docker-mastery/tree/main/swarm-app-1">Instructions</a></h3>
<ul>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="true" disabled=""> Voting App</li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="true" disabled=""> 1 volume, 2 networks, 5 services needed</li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="true" disabled=""> Create the commands needed, spin up services, and test app</li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="true" disabled=""> Everything is using Docker Hub images</li>
</ul>
<h3 id="commands">Commands:</h3>
<p>All builds are inside of <code>node1</code> machine.<br>
<code>web-app.sh</code>:</p>
<pre><code># docker create 'frontend', 'backend' networks
docker network create --driver overlay frontend
dcoker network create --driver overlay backend

# create 5 services
# vote:
docker service create --name vote --network frontend --replicas 2 -p 8080:80 bretfisher/examplevotingapp_vote

# redis:
docker service create --name redis --network frontend redis:alpine

# worker:
docker service create --name worker --network frontend --network backend bretfisher/examplevotingapp_worker:java

# db
docker service create --name db --network backend -e POSTGRES_HOST_AUTH_METHOD=trust --mount type=volume,source=db-data,target=/var/lib/postgresql/data postgres

# result
docker service create --name result --network backend -p 5001:80 bretfisher/examplevotingapp_result
</code></pre>
<h3 id="results">Results:</h3>
<p><code>docker service ls</code>：</p>
<pre><code>ID                  NAME                MODE                REPLICAS            IMAGE                                       PORTS
v2keko676x2t        db                  replicated          1/1                 postgres:latest
lgjsrw35sua7        redis               replicated          1/1                 redis:alpine
ixo610ozwcbc        result              replicated          1/1                 bretfisher/examplevotingapp_result:latest   *:5001-&gt;80/tcp
j4pv3dspwww4        vote                replicated          2/2                 bretfisher/examplevotingapp_vote:latest     *:8080-&gt;80/tcp
kihbsvh7xpxw        worker              replicated          1/1                 bretfisher/examplevotingapp_worker:java
</code></pre>
<h3 id="testing">Testing:</h3>
<p><code>docker service ps vote</code> , <code>ps redis</code>,  <code>ps db</code>, <code>ps worker</code>, <code>ps result</code><br>
On browser:<br>
<ins>192.168.99.100:8080</ins>, <ins>192.168.99.100:5001</ins></p>
<h2 id="create-a-stack-with-secrets-and-deploy">Create A Stack with Secrets and Deploy</h2>
<h3 id="installation-notes-2">Installation Notes:</h3>
<ul>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="true" disabled=""> Use<br>
<a href="https://github.com/BretFisher/udemy-docker-mastery/tree/main/compose-assignment-2/answer">compose-assignment-2</a>.</li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="true" disabled=""> Rename image back to official drupal.</li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="true" disabled=""> Remove build.</li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="true" disabled=""> Add secret via <code>external:</code>.</li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="true" disabled=""> Use environment variable <code>POSTGRES_PASSWORD_FILE</code>.</li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="true" disabled=""> Add secret via cli <code>echo "&lt;pw&gt;" | docker secret create psql_pw -</code></li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="true" disabled=""> Copy compose into a new yml file on your swarm node1.</li>
</ul>
<h3 id="commands-1">Commands:</h3>
<p><em>dev environment</em>: <code>node1</code></p>
<p>Complete all changes and copy to <a href="https://github.com/BretFisher/udemy-docker-mastery/tree/main/secrets-assignment-1/answer">secrets-assignment-1</a>.<br>
Navigate to <code>secrets-assignment-1</code> directory:<br>
<code>echo "&lt;pw&gt;" | docker secret create psql_pw -</code> =&gt; create password external via cli.<br>
<code>docker stack deploy -c docker-compose.yml mydrupal</code></p>
<h3 id="testing-1">Testing:</h3>
<p>Test site: 192.168.99.103:8080</p>

