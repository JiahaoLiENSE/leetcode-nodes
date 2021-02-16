---


---

<p>To check new version before working on docker:<br>
<code>docker version</code> or <code>sudo docker version</code></p>
<p>To show docker commands list:<br>
<code>docker</code></p>
<p>To view docker info:<br>
<code>docker info</code></p>
<p>To create free open source web server - <strong>Nginx</strong>:<br>
<code>docker container run --publish 8888:80 nginx</code><br>
or<br>
<code>docker container run --publish 80:80 nginx</code><br>
<ins>Behind the scenes:</ins> <em><strong>looks</strong> for image cache locally, if does not find, then <strong>looks</strong> for remote image repository. <strong>Downloads</strong> latest version - nginx as default. <strong>Creates</strong> new container and <strong>Gives</strong> virtual IP 80 on host and 80 in container traffic. <strong>Starts</strong> container by using the CMD in image Dockerfile</em></p>
<p>To list container or images:<br>
<code>docker ps</code></p>
<p>To stop running container:<br>
<code>docker container stop &lt;id&gt;/&lt;name&gt;</code></p>
<p>To view docker container logs:<br>
<code>docker container logs 'container name'</code></p>
<p>To remove/delete image:<br>
<code>docker container rm -f 'container id(s)</code></p>
<p>To change the defaults:<br>
<code>docker container run --publish 8080:80 --name webhost -d nginx:1:11 nginx -T</code><br>
<ins>Notes:</ins> <em>8080:80 is host listening port; 1.11 is version of image.</em></p>
<p>To download mongo image:<br>
<code>docker run --name mongo -d mongo</code></p>
<p>To download mysql image:<br>
<code>docker container run -d -p 3306:3306 --name db -e MYSQL_ROOT_RANDOM_PASSWORD=yes mysql</code></p>
<p>To download httpd image:<br>
<code>docker container run -d --name webserver -p 8080:80 httpd</code></p>
<p>To download Nginx proxy web server image:<br>
<code>docker container run -d --name proxy -p 80:80 nginx</code></p>
<p>Process list in one container: <code>docker container top</code><br>
Details of one container config: <code>docker container inspect</code><br>
Performance stats for all live containers: <code>docker container stats</code></p>
<p><code>docker container run -it --name proxy nginx bash</code><br>
<ins>Notes:</ins> <strong>thats will let you go inside of that image and do normall shell commands;</strong> <code>-t</code> simulates a real terminal, like what SSH does; <code>-i</code> keeps session open to recieve terminal input. If run with <code>-it</code>, it will give you a terminal inside the running container.</p>
<p>To download ubuntu image:<br>
<code>docker container run -it --name ubuntu ubuntu</code><br>
<ins>Notes:</ins> ubuntu command shell default is <code>bash</code>.<br>
To install <code>curl</code> package inside ubuntu image:<br>
<code>apt-get update</code><br>
<code>apt-get install -y curl</code><br>
To exit that container:<br>
<code>exit</code><br>
To restart that container:<br>
<code>docker container start -ai ubuntu</code><br>
<ins>Notes:</ins> <code>-a</code> Attach STDOUT/STDERR and forward signals; <code>-i</code> Attach container’s STDIN.<br>
To run additional process in running container:<br>
<code>docker container exec -it mysql</code></p>
<p>To install a small security-focused distribution - Alpine Linux image:<br>
<code>docker pull alpine</code><br>
To run shell inside apline container:<br>
<code>docker container run -it alpine sh</code><br>
<ins>Notes:</ins> Alpine is extremely small and <code>sh</code> is default shell tool.</p>
<p>To see which port number is using for traffic network:<br>
<code>docker container port &lt;image_name&gt;</code><br>
To get virtual network IP address:<br>
<code>docker container inspect --format '{{ .NetworkSettings.IPAddress }}' &lt;image_name&gt;</code><br>
To compare physical/actual IP address:<br>
<code>ifconfig en0</code></p>
<p>To show networks:<br>
<code>docker network ls</code><br>
To inspect network for networks, IP, mounts, and current status:<br>
<code>docker network inspect 'default drive in docker'</code><br>
<em>By default, docker has <code>bridge</code>, <code>host</code> drivers. <code>bridge</code> is default docker virtual network, that is NAT behind the host IP; <code>host</code> gains performance by skipping virtual networks but sacrifices security of container model</em><br>
To create new virtual network drive for you to attach containers to:<br>
<code>docker network create my_app_net</code></p>
<p>To download image into new created/specified virtual network:<br>
<code>docker container run -d --name new_nginx --network my_app_net nginx</code></p>
<p>To connect specific network with another:<br>
<code>docker network connect &lt;one_bridge_id&gt; &lt;another_bridge_id&gt;</code><br>
Then see whether they are connected:<br>
<code>docker network inspect &lt;another_bridge_id&gt;</code><br>
To disconnect them:<br>
<code>docker network disconnect &lt;one_bridge_id&gt; &lt;another_bridge_id&gt;</code></p>
<p>To communicate/ping other networks under the same bridge network:<br>
<code>docker container exec -it &lt;container_name&gt; ping &lt;container_name&gt;</code></p>
<p>To quick install, get inside images, and cleanup images:<br>
<code>docker container run --rm -it &lt;image_name&gt; bash</code><br>
Type:<br>
<code>exit</code> that will auto clean up images in the docker.</p>
<p>DNS Round Robin Test:<br>
To download and research, use to give them an additional DNS name:<br>
<code>docker network create dude</code>: to create bridge.<br>
<code>docker container run -d --net dude --network-alias search elasticsearch:2</code><br>
Run it two times to create two images:<br>
<code>docker container run -d --net dude --network-alias search elasticsearch:2</code><br>
DNS to see the two containers list for the same DNS name(will give two dns ip addresses):<br>
<code>docker container run --rm -net dude alpine nslookup search</code><br>
Using centos curl tool to search elsticsearch:2 data in port 9200:<br>
<code>docker container run --rm --net dude centos curl -s search:9200</code></p>
<p>To get lastest images:<br>
<code>docker pull &lt;image_name&gt;</code></p>
<p>To inspect all info about images:<br>
<code>docker image inspect &lt;image_name&gt;</code></p>
<p>To create own image:<br>
<code>docker image tag &lt;offical_default_image_name&gt; &lt;dockerID_name&gt;/&lt;offical_default_image_name&gt;</code><br>
<strong>Example:</strong><br>
<code>docker image tag nginx jiahao88dockerontheway/nginx</code><br>
<strong>result:</strong><br>
Repository =&gt; jiahao88dockerontheway/nginx<br>
Tag =&gt; latest<br>
image id =&gt; same as offical one</p>
<p>To create own tag with created image:<br>
<code>docker image tag jiahao88dockerontheway/nginx jiahao88dockerontheway/nginx:testing</code></p>
<p>To push own image to docker hub:<br>
<code>docker login</code><br>
<code>docker image push &lt;image_name&gt;:tag</code><br>
<code>docker logout</code></p>
<p>To build new image with nginx dockerfile:<br>
Run with this dockerfile:<br>
<a href="https://github.com/nginxinc/docker-nginx/blob/0dc809fa606828a78087cd0a824bed06268d73e0/mainline/buster/Dockerfile">official nginx github</a><br>
<code>docker image build -t customnginx .</code><br>
<ins>Note:</ins> <code>.</code> means current dir; <code>-t</code> means TAG<br>
To run and copy a custome file into the image at build time:<br>
Run with this dockerfile:<br>
<a href="https://github.com/BretFisher/udemy-docker-mastery/blob/main/dockerfile-sample-1/Dockerfile">udemy-docker-mastery/dockerfile-sample-2</a><br>
<code>docker image build -t nginx-with-html .</code><br>
<code>docker container run -p 8888:80 --rm nginx-with-html</code><br>
<ins>Note:</ins> build new image - nginx-with-html with latest nginx; <code>--rm</code> run container and exit with deleting action.</p>
<p>To clean up unused images in docker system:<br>
<code>docker image prune -a</code> to clean up just “dangling” images;<br>
<code>docker system prune</code> to clean up everything.</p>
<p><strong>Data Volume</strong>: A data volume is a specially-designated directory within one or more containers that bypasses the Union File System. Data volumes provide several useful features for persistent or shared data.</p>
<ul>
<li>Volumes are initialized when a container is created. If the container’s base image contains data at the specified mount point, that existing data is copied into the new volume upon volume initialization. (Note that this does not apply when mounting a host directory.)</li>
<li>Data volumes can be shared and reused among containers.</li>
<li>Changes to a data volume are made directly.</li>
<li>Changes to a data volume will not be included when you update an image.</li>
<li>Data volumes persist even if the container itself is deleted.</li>
</ul>
<p>It’s hard to recognize volumes are associated with which images, <strong>but it can be specified with name by</strong>:<br>
<code>docker container run -d --name mysql -e MYSQL_ALLOW_EMPTY_PASSWORD=True -v mysql-db:/var/lib/mysql mysql</code><br>
<ins>Note:</ins> <code>/var/lib/lib</code> where is default location volume stores.</p>
<p><strong>Docker Volume Create</strong> =&gt; <code>docker volume create --help</code><br>
<ins>Note</ins>: <code>docker volume create</code> is required to do this before <code>docker run</code> to use custom drivers and labels.</p>
<p><strong>Bind Mounting</strong>: When you use a bind mount, a file or directory on the <em>host machine</em> is mounted into a container. The file or directory is referenced by its absolute path on the host machine.</p>
<p>To run container with <strong>custom html file</strong> in the host:<br>
<code>docker container run -d --name nginx -p 8080:80 -v $(pwd):/usr/share/nginx/html nginx</code><br>
<ins>Note</ins>: <code>$(pwd)</code> print working directory and replace this command with this path. This will mounts any changes(adding files, for example) and copy/share to the host even I do not need to touch the shell of the container.<br>
<code>$(pwd)</code> =&gt; current directory path; container <em>mount source</em>;<br>
<code>/usr/share/nginx/html</code>  =&gt; container <em>mount destination</em><br>
By comparing to run container with <strong>default host</strong>:<br>
<code>docker container run -d --name nginx2 -p 8888:80 nginx</code></p>
<h2 id="docker-compose-cli">Docker Compose CLI:</h2>
<p><code>docker-compose up</code> set up volumes/networks and start all containers<br>
<code>docker-compose down</code> stop all containers and remove cont/vol/net</p>
<p>To run nginx webserver with docker compose file - <a href="https://github.com/BretFisher/udemy-docker-mastery/tree/main/compose-sample-1">docker-compose.yml</a>:<br>
<code>docker-compose up</code> or <code>docker-compose up -d</code>(run it in background)</p>
<p>To show docker compose info:<br>
<code>docker-compose ps</code></p>
<p>To shut down and remove all containers:<br>
<code>docker-compose down</code></p>
<h2 id="swarm-cluster">Swarm Cluster</h2>
<h3 id="basic-cmds">Basic CMDs:</h3>
<p>Activate swarm:<br>
<code>docker swarm init</code><br>
Behind init:</p>
<ul>
<li>Lots of PKI and security automation
<ul>
<li>Root signing certificate created for our Swarm</li>
<li>Certificate is issued for first mananger node</li>
<li>Join tokens are created</li>
</ul>
</li>
<li>Raft database created to store root CA, configs nd secrets</li>
</ul>
<p>Swarm Nodes:<br>
<code>docker node ls</code></p>
<p>Swarm Services:<br>
<code>docker service ls</code><br>
To add service and ping google server via apline image<br>
<code>docker service create apline ping 8.8.8.8</code><br>
Check avaliable services:<br>
<code>docker service ls</code></p>
<pre><code>ID             NAME              MODE         REPLICAS   IMAGE           PORTS
9irinpmn8bth   nice_kowalevski   replicated   1/1        alpine:lates
</code></pre>
<p>Includes container <code>id</code>, <code>random tag name</code> and <code>1/1</code> means one running service of totally one service is running.</p>
<p>Scale docker services (<a href="#swarm-update-example">Scale command updates</a>):<br>
<code>docker service update &lt;id&gt; --replicas 3</code> creates 3 replicas services</p>
<p>Results for <code>docker service ls</code>:</p>
<pre><code>ID             NAME              MODE         REPLICAS   IMAGE           PORTS
9irinpmn8bth   nice_kowalevski   replicated   3/3        alpine:latest
</code></pre>
<p>Results for <code>docker service ps 9irinpmn8bth</code></p>
<pre><code>ID             NAME                IMAGE           NODE             DESIRED STATE   CURRENT STATE            ERROR     PORTS
u3mzanpgptsc   nice_kowalevski.1   alpine:latest   docker-desktop   Running         Running 2 hours ago
n77qu2ixdwze   nice_kowalevski.2   alpine:latest   docker-desktop   Running         Running 57 seconds ago
r91buoez3e0e   nice_kowalevski.3   alpine:latest   docker-desktop   Running         Running 57 seconds ago
</code></pre>
<p>To change or replace services without taking whole container down:<br>
<code>docker service update</code> <code>--help</code> for more info about commands</p>
<p>To take one of services down:<br>
<code>docker container rm -f &lt;service_name&gt;.&lt;id&gt;</code><br>
Results:</p>
<pre><code> ID             NAME                    IMAGE           NODE             DESIRED STATE   CURRENT STATE            ERROR                         PORTS
gop508tzu8ej   nice_kowalevski.1       alpine:latest   docker-desktop   Running         Running 40 seconds ago
7j79jgmem8tn    \_ nice_kowalevski.1   alpine:latest   docker-desktop   Shutdown        Failed 45 seconds ago    "task: non-zero exit (137)"
u3mzanpgptsc    \_ nice_kowalevski.1   alpine:latest   docker-desktop   Shutdown        Failed 2 minutes ago     "task: non-zero exit (137)"
n77qu2ixdwze   nice_kowalevski.2       alpine:latest   docker-desktop   Running         Running 12 minutes ago
r91buoez3e0e   nice_kowalevski.3       alpine:latest   docker-desktop   Running         Running 12 minutes ago
</code></pre>
<p>It would shutdown one of containers for a whole and re-running again. And that won’t let our services server down forever.</p>
<p>To clean/remove the entire service:<br>
<code>docker service rm &lt;id&gt;</code><br>
Note: it would take a while to remove because backend system have not yet gone through the process real quick.</p>
<h2 id="create-3-node-swarm-cluster">Create 3-Node Swarm Cluster:</h2>
<p>Three options to install <code>docker machine</code>:</p>
<ol>
<li><a href="http://play-with-docker.com">play-with-docker.com</a> =&gt; only need browser, but reset 4 hrs</li>
<li>docker-machine + VirtualBox =&gt; free and runs locally, but requires a machine with 8GB memory</li>
<li>Digtial Ocean + Docker install =&gt; costs $5-10/node/month</li>
<li>Roll your own =&gt; install docker anywhere with <a href="http://get.docker.com">get.docker.com</a></li>
</ol>
<p>Option 2:<br>
Install <code>docker-machine</code> from <a href="https://docs.docker.com/machine/install-machine/">offical</a>.</p>
<p><strong>Create Node Machines</strong>:<br>
<code>docker-machine create node1</code><br>
<strong>Access node1 machine</strong>:<br>
<code>docker-machine ssh node1</code><br>
or<br>
<strong>Access node1 environment</strong>:<br>
<code>docker-machine env node</code></p>
<pre><code>export DOCKER_TLS_VERIFY="1"
export DOCKER_HOST="tcp://192.168.99.100:2376"
export DOCKER_CERT_PATH="/Users/Andy/.docker/machine/machines/node1"
export DOCKER_MACHINE_NAME="node1"
# Run this command to configure your shell:
# eval $(docker-machine env node1)
</code></pre>
<p><strong>To use env variable</strong>:<br>
<code>eval $(docker-machine env node1)</code><br>
<code>docker-machine info</code></p>
<p><strong>Swarm Manager Node(node1) init</strong>:<br>
<code>docker-machine ssh node1</code><br>
<code>docker swarm init --advertise-addr &lt;ip_address&gt;</code></p>
<pre><code>To add a worker to this swarm, run the following command:

    docker swarm join --token SWMTKN-1-3u1q8q5iy8g3x3xwgpm7yv5g495i3wokl66bjugmxtfm7ubjnk-3l8kdai1hpcchchqeua7hou45 192.168.99.100:2377

To add a manager to this swarm, run 'docker swarm join-token manager' and follow the instructions.
</code></pre>
<p><strong>Add workers(node2, node3)</strong>:<br>
<code>exit</code> =&gt; exit node1 env;<br>
<code>docker-machine create node2</code> =&gt; create node2 machine;<br>
<code>docker-machine ssh node2</code> =&gt; access node2 machine;</p>
<p><code>docker swarm join --token SWMTKN-1-3u1q8q5iy8g3x3xwgpm7yv5g495i3wokl66bjugmxtfm7ubjnk-3l8kdai1hpcchchqeua7hou45 192.168.99.100:2377</code> =&gt; join node2 as a worker;</p>
<p><code>exit</code> =&gt; exit node2 env;<br>
<code>docker-machine create node3</code> =&gt; create node3 machine;<br>
<code>docker-machine ssh node2</code> =&gt; access node2 machine;</p>
<p><code>docker swarm join --token SWMTKN-1-***</code> =&gt; join node3 as a worker;<br>
<code>exit</code> and <code>docker-machine ssh node1</code><br>
<code>docker node ls</code> =&gt; to see all nodes’ machine.</p>
<p><strong>Results</strong>:</p>
<pre><code>ID                            HOSTNAME            STATUS              AVAILABILITY        MANAGER STATUS      ENGINE VERSION
b830mt9mlgcwfs5di29356x38 *   node1               Ready               Active              Leader              19.03.12
c3mmz36m8paamy60dx8je0r70     node2               Ready               Active                                  19.03.12
</code></pre>
<p><strong>To promote node2, for example from a worker to a manager</strong>:<br>
Access into node1 manager shell:<br>
<code>docker node update --help</code> =&gt; for update commands help;<br>
<code>docker node update --role manager node2</code> =&gt; to promote node2 as manager.</p>
<p><a href="https://docs.docker.com/engine/swarm/manage-nodes/">More info for node action.</a></p>
<p><strong>Another way to promote as a manager(node3)</strong>:<br>
Inside node1 shell:<br>
<code>docker swarm join-token manager</code> =&gt; give us a manager join-token</p>
<pre><code>To add a manager to this swarm, run the following command:

docker swarm join --token SWMTKN-1-***
</code></pre>
<p>Copy and paster inside of node3 shell:<br>
<code>docker swarm join --token SWMTKN-1-***</code></p>
<p><strong>Testing: create &amp; operate services controlled by node1 manager</strong><br>
Inside of node1 shell:<br>
<code>docker service create --replicas 3 alpine ping 8.8.8.8</code></p>
<pre><code>ID                  NAME                MODE                REPLICAS            IMAGE               PORTS
u5q9rr3aeg5x        amazing_saha        replicated          3/3                 alpine:latest
</code></pre>
<p><code>docker service ps &lt;service_name&gt;</code><br>
<code>docker service ps amazing_saha</code></p>
<p><strong>Result</strong>:</p>
<pre><code>n8kqm4iqphds        amazing_sah.1   alpine:latest       node2               Running             Running 38 seconds ago
j3qq0fgh0mg8        amazing_sah.2   alpine:latest       node1               Running             Running 38 seconds ago
</code></pre>
<h2 id="overlay-networking-comunicates-across-all-nodes-">Overlay Networking (Comunicates across all nodes ):</h2>
<p><strong>Create overlay network in node1</strong>:<br>
<code>docker-machine ssh node1</code><br>
<code>docker network create --driver overlay mydrupal</code></p>
<pre><code>NETWORK ID          NAME                DRIVER              SCOPE
54cd97231ca8        bridge              bridge              local
d92ccdde9f10        docker_gwbridge     bridge              local
535c6cb6ab9d        host                host                local
ypvvv70kyzws        ingress             overlay             swarm
ngksqww3tegn        mydrupal            overlay             swarm
2c0e30348887        none                null                local
</code></pre>
<p><strong>Create Postgresql service with created overlay network</strong>:<br>
<code>docker service create --name psql --network mydrupal -e POSTGRES_PASSWORD=mypass postgres</code></p>
<p><code>docker service ps psql</code></p>
<pre><code>ID                  NAME                IMAGE               NODE                DESIRED STATE       CURRENT STATE            ERROR               PORTS
m2r6756lk1nv        psql.1              postgres:latest     node1               Running             Running 19 seconds ago
</code></pre>
<p><strong>Create Drupal service with created overlay network</strong>:<br>
<code>docker service create --name drupal --network mydrupal -p 8080:80 drupal</code></p>
<p><code>docker service ps psql</code></p>
<pre><code>ID                  NAME                IMAGE               NODE                DESIRED STATE       CURRENT STATE           ERROR               PORTS
ujwotba6ozia        drupal.1            drupal:latest       node2               Running             Running 2 minutes ago
</code></pre>
<p><strong>Testing</strong>:<br>
node1 =&gt; 192.168.99.100:8080<br>
node2 =&gt; 192.168.99.101:8080<br>
node3 =&gt; 192.168.99.102:8080</p>
<h2 id="routing-mesh">Routing Mesh</h2>
<ul>
<li>Routes ingress (incoming) packets for a service to proper task</li>
<li>Spans all nodes in Swarm</li>
<li>Uses IPVS from Linux Kernel</li>
<li>Load balances Swarm Services across their tasks</li>
<li>Two working way:
<ul>
<li>Container-to-container in a Overlay network (uses VIP)</li>
<li>External traffic incoming to published ports (all nodes listen)</li>
</ul>
</li>
<li>Stateless load balancing</li>
<li>Load balance is at OSI layer 3 (TCP), not Layer 4 (DNS)</li>
<li>Both limitation can be overcome with:
<ul>
<li>Nginx or HAProxy LB proxy, or</li>
<li>Docker Enterpise Edition, which comes with bulit-in L4 web proxy</li>
</ul>
</li>
</ul>
<h2 id="stacks">Stacks</h2>
<ul>
<li>New layer of abstraction to Swarm called Stacks</li>
<li>Accept compose file as definition of services, networks, and volumes</li>
<li>We use <code>docker stack deploy</code> rather than <code>docker service create</code></li>
<li>Stacks manage all those objects for us, including overlay network per stack. Adds stack name to start of their name</li>
<li>New <code>deploy</code> key in composefile. Can not do <code>build</code></li>
<li>Compose now ignores <code>deploy</code>, Swarm ignores `build</li>
<li><code>docker-compose</code> cli not needed on Swarm server</li>
</ul>
<h3 id="swarm-stacks-and-compose-file">Swarm Stacks and Compose File:</h3>
<p><em>dev environment</em>: <code>node1</code></p>
<p><strong>Compose File <a href="https://github.com/BretFisher/udemy-docker-mastery/tree/main/swarm-stack-1">Reference</a></strong>:<br>
<code>docker stack deploy -c example-voting-app-stack.yml voteapp</code><br>
<ins>Note:</ins> <code>-c</code> = <code>--compose</code><br>
<strong>Result:</strong></p>
<pre><code>docker@node1:/Users/Andy/Downloads/Projects/udemy-docker-mastery/swarm-stack-1$ docker stack deploy -c example-voting-app-stack.yml voteapp
Creating network voteapp_backend
Creating network voteapp_default
Creating network voteapp_frontend
Creating service voteapp_worker
Creating service voteapp_visualizer
Creating service voteapp_redis
Creating service voteapp_db
Creating service voteapp_vote
Creating service voteapp_result
</code></pre>
<p><code>docker stack ps voteapp</code>:</p>
<pre><code>ID                  NAME                   IMAGE                                       NODE                DESIRED STATE       CURRENT STATE           ERROR               PORTS
xh1zht4breez        voteapp_result.1       bretfisher/examplevotingapp_result:latest   node3               Running             Running 5 minutes ago
lif9dhtro6e5        voteapp_vote.1         bretfisher/examplevotingapp_vote:latest     node3               Running             Running 5 minutes ago
5i6hnhjiwx51        voteapp_db.1           postgres:13.0                               node1               Running             Running 5 minutes ago
o76o7xvz4s9t        voteapp_redis.1        redis:alpine                                node2               Running             Running 6 minutes ago
awtye6wt767m        voteapp_visualizer.1   dockersamples/visualizer:latest             node1               Running             Running 4 minutes ago
r1cb4fmoly6w        voteapp_worker.1       bretfisher/examplevotingapp_worker:java     node1               Running             Running 5 minutes ago
gjie3joga48h        voteapp_vote.2         bretfisher/examplevotingapp_vote:latest     node2               Running             Running 6 minutes ago
</code></pre>
<p><code>docker stack service voteapp</code>:</p>
<pre><code>8mmx2s2uidc5        voteapp_visualizer   replicated          1/1                 dockersamples/visualizer:latest             *:8080-&gt;8080/tcp
innnfzdnxno7        voteapp_redis        replicated          1/1                 redis:alpine                                *:30000-&gt;6379/tcp
npbem9tsnsw0        voteapp_worker       replicated          1/1                 bretfisher/examplevotingapp_worker:java
s6avij4b3q3s        voteapp_vote         replicated          2/2                 bretfisher/examplevotingapp_vote:latest     *:5000-&gt;80/tcp
y50yixdpbugu        voteapp_result       replicated          1/1                 bretfisher/examplevotingapp_result:latest   *:5001-&gt;80/tcp
z80jtd62ryfb        voteapp_db           replicated          1/1                 postgres:13.0
</code></pre>
<p><code>docker network ls</code>:</p>
<pre><code>54cd97231ca8        bridge              bridge              local
d92ccdde9f10        docker_gwbridge     bridge              local
535c6cb6ab9d        host                host                local
ypvvv70kyzws        ingress             overlay             swarm
2c0e30348887        none                null                local
r7isxjant26t        voteapp_backend     overlay             swarm
kw0j8qby29sf        voteapp_default     overlay             swarm
59uv7mlkgc64        voteapp_frontend    overlay             swarm
</code></pre>
<p><strong>Test on Browser:</strong><br>
vote site =&gt; 192.168.99.100:5000,<br>
result site =&gt; 192.168.99.100:5001,<br>
visualizer site =&gt; 192.168.99.100:8080</p>
<p><strong>Update compose-file:</strong><br>
<code>docker stack deploy -c example-voting-app-stack.yml voteapp</code></p>
<h2 id="secrets-storage">Secrets Storage</h2>
<ul>
<li>Secret:
<ul>
<li>Usernames and passwords</li>
<li>TLS certificates and keys</li>
<li>SSH keys</li>
<li>Not to be on the site</li>
</ul>
</li>
<li>Supports generic strings or binary content up to 500kb in size</li>
<li>Does not require apps to be rewrriten</li>
<li>Swarm Raft DB is encrypted on disk</li>
<li>Only stored on Manager nodes</li>
<li>Secrets are first stored in Swarm, then assigned to a Service</li>
<li>Only containers in assigned services can see them</li>
<li>In-memory fs</li>
<li><code>/run/secrets/&lt;secret_name&gt;</code> or <code>/run/secrets/&lt;secret_alias&gt;</code></li>
</ul>
<h3 id="create-secret">Create Secret:</h3>
<p><em>dev environment</em>: <code>node1</code></p>
<p><a href="https://github.com/BretFisher/udemy-docker-mastery/tree/main/secrets-sample-1">secrets-sample-1</a><br>
Navigate to <code>secret-sample-1</code> directory:<br>
<code>docker secret create psql_user psql_user.txt</code> =&gt; put the secret username (will produce an id) into DB.<br>
<code>echo "myDBpassWORD" | docker secret create psql_pass -</code> =&gt; put the secret password (will produce an id) into DB. <code>-</code> represents read standard input.<br>
<ins>Note</ins>: Drawback: username and password will store in local machine that is not good for security but local dev. Usually, it will use remote API to create, and store them.</p>
<h3 id="create-service-and-map-secret-to-it">Create Service and Map Secret to it:</h3>
<p><code>docker service create --name psql --secret psql_user --secret psql_pass -e POSTGRES_PASSWORD_FILE=/run/secrets/psql_pass -e POSTGRES_USER_FILE=/run/secrets/psql_user postgres</code></p>
<p><strong>To Check whether it works</strong>:<br>
<code>docker service ps psql</code> =&gt; if container does not repeatly re-create service, it works.</p>
<p>Or<br>
<code>docker exec -it &lt;container_name&gt; bash</code>,<br>
<code>ls /run/secrets/psql_user</code>  -&gt; <code>cat psql_user</code> =&gt; if psql_user is there, it works.</p>
<p>Or<br>
<code>exit</code>,<br>
<code>docker logs &lt;container_name&gt;</code> =&gt; if postgres runs correctly, it works.</p>
<h2 id="secrets-with-swarm-stacks">Secrets with Swarm Stacks</h2>
<p><em>dev environment</em>: <code>node1</code></p>
<p><strong>Command</strong>:<br>
<a href="https://github.com/BretFisher/udemy-docker-mastery/tree/main/secrets-sample-2">secrets-sample-2</a><br>
Navigate to <code>secrtes-sample-2</code> directory:<br>
<code>docker stack deploy -c docker-compose.yml mydb</code></p>
<p><strong>Result</strong>:</p>
<pre><code>ID                          NAME                 DRIVER              CREATED              UPDATED
8o2dysf9w7n5y1590mvzadivy   mydb_psql_password                       About a minute ago   About a minute ago
xwacldtf51k8l2fpbncd7fq81   mydb_psql_user                           About a minute ago   About a minute ago
</code></pre>
<p><strong>Remove all services and secrets</strong>:<br>
<code>docker stack rm mydb</code></p>
<h2 id="using-secrets-with-local-docker-compose">Using Secrets with Local Docker Compose</h2>
<p>Local development with secrets (not in swarm node).<br>
<a href="https://github.com/BretFisher/udemy-docker-mastery/tree/main/secrets-sample-2">secrets-sample-2</a>.</p>
<p>Navigate into <code>secrets-sample-2</code> directory:<br>
<code>docker-compose up -d</code> =&gt; <strong>not inside of swarm node</strong>.<br>
<code>docker-compose exec psql cat /run/secrets/psql_user</code><br>
<ins>How it works</ins>: Behind the scene, bind mounts at run time that actual file on my hard drive to container, but it is totally not secure.</p>
<h2 id="full-app-lifecycle-with-compose">Full App Lifecycle With Compose</h2>
<ul>
<li>Multiple Compose files</li>
<li>Using multiple Compose files enables you to customize a Compose application for differnet environments or different workflows like production-like environment (maybe production, staging, or CI).</li>
<li><code>docker-compose.yml</code> =&gt; Start with a base file that defines the canonical configuration for the services.</li>
<li><code>docker-compose.override.yml</code> =&gt; the development configuration exposes some ports to the host, mounts our code as a volume, and builds the web image. And it reads the overrides automatically when run <code>docker-compose up</code>.</li>
<li><code>docker-compose.prod.yml</code> =&gt; Use this Compose app in a production environment. So, create another override file  (which might be stored in different git repo or managed by a different team).</li>
<li><code>docker-compose.admin.yml</code> =&gt; Add a new service to run the database export or backup.</li>
<li><a href="https://docs.docker.com/compose/extends/#multiple-compose-files">More sources on using multiple docker compose files</a>. And <a href="https://docs.docker.com/compose/production">More sources on using compose in production</a>.</li>
</ul>
<h2 id="swarm-update-example">Swarm Update Example</h2>
<p>Just update the image used to a newer version:<br>
<code>docker service update --image myapp:1.2.1 &lt;servicename&gt;</code></p>
<p>Adding an environment variable and remove a port at the same time as updating image:<br>
<code>docker service update --env-add NODE_ENV=production --publish-rm 8080</code><br>
or<br>
Just change port:<br>
<code>docker service update --publish-rm 8080 --publish-add 9090:80 &lt;servicename&gt;</code></p>
<p>Change number of replicas of two services:<br>
<code>docker service scale web=8 api=6</code></p>
<p>Updates in Stack Files:<br>
<code>docker stack deploy -c file.yml &lt;stackname&gt;</code> =&gt; same command. just edit the YML file</p>
<h2 id="docker-healthchecks">Docker Healthchecks</h2>
<ul>
<li>Docker engine will exec’s the command in the container. e.g. <code>curl localhost</code></li>
<li>It expects <code>exit 0</code> (OK), or <code>exit 1</code> (Error)</li>
<li>Three contaienr states: starting, healthy, unhealthy</li>
<li>Healthcheck status shows up in <code>docker container ls</code></li>
<li>Check last 5 healthchecks with <code>docker container inspect</code></li>
<li>Docker run does nothing with healthchecks if it is unhealthy</li>
<li>Services will replace tasks if they fail healthcheck</li>
<li>Serives update wait for them before continuing</li>
<li>Options for healthcheck command:
<ul>
<li><code>--interval=DURATION (default: 30s)</code></li>
<li><code>--timeout=DURATION (default: 30s)</code></li>
<li><code>--start-period=DURATION (default: 0s)</code></li>
<li><code>--retries=N (default: 3)</code></li>
</ul>
</li>
<li>Basic command using default options:
<ul>
<li><code>HEALTHCHECK curl -f http://localhost/ || false</code></li>
</ul>
</li>
<li>Custom options with the command:
<ul>
<li><code>HEALTHCHECK --timeout=2s --interval=3s --retries=3 CMD curl -f http://localhost/ || exit 1</code></li>
</ul>
</li>
</ul>
<h3 id="healthcheck-in-php-nginx-dockerfile">Healthcheck in PHP Nginx Dockerfile:</h3>
<pre><code>FROM your-nginx-php-fpm-combo-image

HEALTHCHECK --interval=5s --timeout=3s CMD curl -f http://localhost/ping || exit 1
</code></pre>
<h3 id="healthcheck-in-postgres-dockerfile">Healthcheck in Postgres Dockerfile:</h3>
<pre><code>FROM postgres

# specify real user with -U to prevent errors in log

HEALTHCHECK --interval=5s --timeout=3s CMD pg_isready -U postgres || exit 1
</code></pre>
<h3 id="healthcheck-in-composestack-files">Healthcheck in Compose/Stack Files:</h3>
<pre><code>version: "2.1"
services:
    web:
	    image:nginx
	    healthcheck:
		    test: ["CMD", "curl", "-f", "http://localhost"]
		    interval: 1m30s
		    timeout: 10s
		    retries: 3
		    start_period: 1m #version 3.4 minimum
</code></pre>
<h2 id="run-a-private-docker-registry">Run A Private Docker Registry</h2>
<ul>
<li>Default port 5000</li>
<li>Proper TLS: “Secure by default”; Enable “insecure-regsitry” in engine; Except, localhost(127.0.0.0/8)</li>
</ul>
<h3 id="commands">Commands:</h3>
<p>Create registry image from docker hub (just on local, but backup, see below):<br>
<code>docker container run -d -p 5000:5000 --name registry registry</code></p>
<p>Pull offical <code>hello-world</code> image from docker hub:<br>
<code>docker pull hello-world</code></p>
<p>Re-tag offical image and create own image based on the root of my <strong>local registry (127.0.0.1:5000)</strong>:<br>
<code>docker tag hello-world 127.0.0.1:5000/hello-world</code></p>
<p><strong>Result</strong>:</p>
<pre><code>REPOSITORY                   TAG       IMAGE ID       CREATED         SIZE
postgres                     latest    f51c55ac75ed   5 days ago      314MB
nginx                        latest    daee903b4e43   5 days ago      133MB
registry                     latest    2d4f4b5309b1   5 months ago    26.2MB
127.0.0.1:5000/hello-world   latest    bf756fb1ae65   10 months ago   13.3kB
hello-world                  latest    bf756fb1ae65   10 months ago   13.3kB
</code></pre>
<p><strong>Note:</strong> see <code>hello-world</code> vs <code>127.0.0.1:5000/hello-world</code></p>
<p>Push re-tag image to local registry:<br>
<code>docker push 127.0.0.1:5000/hello-world</code></p>
<p>Remove re-tag image locally:<br>
<code>docker container rm &lt;container_id&gt;</code></p>
<p>Pull the re-tag image from new registry:<br>
<code>docker pull 127.0.0.1:5000/hello-world</code></p>
<p>Re-create regsitry using a bind mount and see how it stores data:<br>
<code>docker container run -d -p 5000:5000 --name registry -v $(pwd)/registry-data:/var/lib/registry registry</code></p>
<p>Check how data stores (<a href="https://github.com/BretFisher/udemy-docker-mastery/tree/main/registry-sample-1">File Reference</a>):<br>
<code>tree register-data/</code></p>
<h2 id="private-docker-registry-with-swarm">Private Docker Registry with Swarm</h2>
<h3 id="what-it-is">What it is</h3>
<p>The Registry is a stateless, highly scalable server side application that stores and lets you distribute Docker images. The Registry is open-source, under the permissive  <a href="https://en.wikipedia.org/wiki/Apache_License">Apache license</a>.</p>
<h3 id="why-use-it">Why use it</h3>
<p>You should use the Registry if you want to:</p>
<ul>
<li>tightly control where your images are being stored</li>
<li>fully own your images distribution pipeline</li>
<li>integrate image storage and distribution tightly into your in-house development workflow</li>
</ul>
<h3 id="tips">Tips</h3>
<ul>
<li>Works the same as localhost</li>
<li>all nodes can see 127.0.0.1:5000</li>
<li>All nodes must be able to access images</li>
<li>Use a hosted SaaS registry if possible</li>
</ul>
<h3 id="commands-1">Commands:</h3>
<p><a href="https://labs.play-with-docker.com/">Online playround</a></p>
<p><strong>Create registry service:</strong><br>
<code>docker service create --name registry --publish 5000:5000 registry</code></p>
<p><strong>See the result</strong>:<br>
Port 5000 on the play-with-docker.<br>
Direct checking on json data: 5000 url + <code>/v2/_catalog</code></p>
<blockquote>
<p><code>{"repositories":[]}</code></p>
</blockquote>
<p><strong>Pull &amp; re-tag image in current registry:</strong><br>
pull image from regisyry:<br>
<code>docker pull hello-world</code></p>
<p>re-tag the image:<br>
<code>docker tag hello-world 127.0.0.1:5000/hello-world</code></p>
<p>push tagged image back to registry:<br>
<code>docker push 127.0.01:5000/hello-world</code></p>
<p><strong>Result</strong>:<br>
<code>{"repositories":["hello-world"]}</code></p>
<p><strong>Create nginx service in registry</strong>:<br>
<code>docker pull nginx</code></p>
<p><code>docker tag nginx 127.0.0.1:5000/nginx</code></p>
<p><code>docker push 127.0.0.1:5000/nginx</code></p>
<p><code>docker service create --name nginx -p 80:80 --replicas 5 --detach=false 127.0.0.1:5000/nginx</code></p>

