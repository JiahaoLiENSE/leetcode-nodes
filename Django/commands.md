---


---

<h2 id="setup">Setup</h2>
<h3 id="requirements">Requirements:</h3>
<ul>
<li><a href="https://nodejs.org/en/">Node.js</a></li>
<li><a href="https://www.python.org/">Python</a></li>
<li><a href="https://docs.python.org/3/library/venv.html">virtualenv</a></li>
</ul>
<h3 id="installation-windows">Installation (Windows):</h3>
<p><code>pip install virtualenv</code><br>
<code>mkdir &lt;project_folder_name&gt;</code><br>
<code>cd &lt;project_folder_name&gt;</code><br>
<code>python -m virtualenv &lt;env_name&gt;</code><br>
<code>cd &lt;env_name&gt;</code></p>
<p>Activate environment:<br>
<code>./scripts/activate</code></p>
<p>Deactivate environment:<br>
<code>deactivate</code></p>
<p>if necessary, remove environment:<br>
<code>rm -rf &lt;each_one_inside_project_folder_name&gt;</code></p>
<h3 id="installation-mac">Installation (Mac):</h3>
<p><code>pip install virtualenv</code><br>
<code>mkdir &lt;project_folder_name&gt;</code><br>
<code>cd &lt;project_folder_name&gt;</code><br>
<code>virtualenv &lt;env_name&gt;</code><br>
<code>cd &lt;env_name&gt;</code></p>
<p>Activate environment:<br>
<code>source /bin/activate</code></p>
<p>Deactivate environment:<br>
<code>deactivate</code></p>
<p>if necessary, remove environment:<br>
<code>rm -rf &lt;each_one_inside_project_folder_name&gt;</code></p>
<h3 id="initialize-sqlite3-database">Initialize sqlite3 database</h3>
<p><code>python manage.py migrate</code><br>
<code>python manage.py createsuperuser</code></p>
<h3 id="migrations">Migrations</h3>
<p>create models:<br>
<code>python manage.py makemigrations</code></p>
<p>create table in sqlite database:<br>
<code>python manage.py sqlmigrate &lt;name&gt;</code></p>
<p>Apply all database changes:<br>
<code>python manage.py migrate</code></p>
<h3 id="playing-with-sqlite-database-via-terminal">Playing with sqlite database via Terminal</h3>
<p><code>python manage.py shell</code></p>
<p>import current model in the database:<br>
<code>from blog.models import Post</code><br>
<code>from django.contrib.auth.models import User</code><br>
Get all users:<br>
<code>User.objects.all()</code><br>
Get specific element:<br>
<code>User.objects.filter('NAME')</code></p>
<h3 id="login-authentication">Login Authentication:</h3>
<p><strong>Loging session check</strong>:<br>
Use <code>login_required</code> decorator from <code>django.contrib.auth.decorators import login_required</code>. However, login docorators only works on functions.</p>
<p><code>views.py</code>:</p>
<pre class=" language-python"><code class="prism  language-python">@login_required
<span class="token keyword">def</span> <span class="token function">profile</span><span class="token punctuation">(</span>request<span class="token punctuation">)</span><span class="token punctuation">:</span>
	<span class="token keyword">return</span> render<span class="token punctuation">(</span>request<span class="token punctuation">,</span> <span class="token string">'users/profile.html'</span><span class="token punctuation">)</span>
</code></pre>
<p><code>settings.py</code>:</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># after login</span>
LOGIN_REDIRECT_URL <span class="token operator">=</span> <span class="token string">'blog-home'</span>
<span class="token comment"># if not logged in, redirect to login page</span>
LOGIN_URL <span class="token operator">=</span> <span class="token string">'login'</span>
</code></pre>
<p><code>LoginRequiredMixin</code>:<br>
Meanwhile, use <code>LoginRequiredMixin</code> from <code>django.contrib.auth.mixins</code>. When using class-based views, you can achieve the same behavior as with <code>login_required</code> by using the <code>LoginRequiredMixin</code>. This mixin should be at the leftmost position in the inheritance list.</p>
<p><code>UserPassesTestMixin</code>:<br>
Mixin that allows you to define a test function which must return True<br>
if the current user can access the view.<br>
<a href="https://docs.djangoproject.com/en/3.1/topics/auth/default/#django.contrib.auth.mixins.UserPassesTestMixin">Usage</a></p>
<h3 id="media">Media</h3>
<p><strong>Profile image</strong>:<br>
<code>models.py</code>:<br>
Two atttributes: <code>models.OneToOneField()</code> and <code>models.ImageField(default=&lt;name of image&gt;, upload_to=&lt;image_path&gt;)</code></p>
<p><code>settings.py</code>:<br>
Create media static urls: <code>MEDIA_ROOT = os.path.join(BASE_DIR, 'media')</code>, <code>MEDIA_URL = '/media/</code></p>
<p><a href="#serving-media">More on Media</a></p>
<h3 id="signals">Signals</h3>
<p><strong>Definition</strong>:<br>
Django includes a “signal dispatcher” which helps allow decoupled applications get notified when actions occur elsewhere in the framework. In a nutshell, signals allow certain <em>senders</em> to notify a set of <em>receivers</em> that some action has taken place. They’re especially useful when many pieces of code may be interested in the same events.</p>
<p><strong>Functions</strong>:<br>
with <code>connect()</code>  method:</p>
<p><code>signals.py</code>:</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">from</span> <span class="token punctuation">.</span>models <span class="token keyword">import</span> Profile

<span class="token keyword">def</span> <span class="token function">create_user_profile</span><span class="token punctuation">(</span>sender<span class="token punctuation">,</span> instance<span class="token punctuation">,</span> created<span class="token punctuation">,</span> <span class="token operator">**</span>kwargs<span class="token punctuation">)</span><span class="token punctuation">:</span>
    <span class="token keyword">if</span> created<span class="token punctuation">:</span>
        Profile<span class="token punctuation">.</span>objects<span class="token punctuation">.</span>create<span class="token punctuation">(</span>user<span class="token operator">=</span>instance<span class="token punctuation">)</span>

<span class="token keyword">def</span> <span class="token function">save_user_profile</span><span class="token punctuation">(</span>sender<span class="token punctuation">,</span> instance<span class="token punctuation">,</span> <span class="token operator">**</span>kwargs<span class="token punctuation">)</span><span class="token punctuation">:</span>
    instance<span class="token punctuation">.</span>profile<span class="token punctuation">.</span>save<span class="token punctuation">(</span><span class="token punctuation">)</span>
</code></pre>
<p><code>apps.py</code>:</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">from</span> django<span class="token punctuation">.</span>apps <span class="token keyword">import</span> AppConfig
<span class="token keyword">from</span> django<span class="token punctuation">.</span>contrib<span class="token punctuation">.</span>auth<span class="token punctuation">.</span>models <span class="token keyword">import</span> User
<span class="token keyword">from</span> django<span class="token punctuation">.</span>db<span class="token punctuation">.</span>models<span class="token punctuation">.</span>signals <span class="token keyword">import</span> post_save

<span class="token keyword">from</span> <span class="token punctuation">.</span>signals <span class="token keyword">import</span> create_user_profile<span class="token punctuation">,</span> save_user_profile

<span class="token keyword">class</span> <span class="token class-name">ProfilesConfig</span><span class="token punctuation">(</span>AppConfig<span class="token punctuation">)</span><span class="token punctuation">:</span>
    name <span class="token operator">=</span> <span class="token string">'users'</span>
    
    <span class="token keyword">def</span> <span class="token function">ready</span><span class="token punctuation">(</span>self<span class="token punctuation">)</span><span class="token punctuation">:</span>
        post_save<span class="token punctuation">.</span>connect<span class="token punctuation">(</span>create_user_profile<span class="token punctuation">,</span> sender<span class="token operator">=</span>User<span class="token punctuation">)</span>
        post_save<span class="token punctuation">.</span>connect<span class="token punctuation">(</span>save_user_profile<span class="token punctuation">,</span> sender<span class="token operator">=</span>User<span class="token punctuation">)</span>
</code></pre>
<p>with decorator  method:</p>
<p><code>signals.py</code>: same as above.</p>
<p><code>apps.py</code>:</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">from</span> django<span class="token punctuation">.</span>apps <span class="token keyword">import</span> AppConfig

<span class="token keyword">class</span> <span class="token class-name">ProfilesConfig</span><span class="token punctuation">(</span>AppConfig<span class="token punctuation">)</span><span class="token punctuation">:</span>
    name <span class="token operator">=</span> <span class="token string">'users'</span>
    
    <span class="token keyword">def</span> <span class="token function">ready</span><span class="token punctuation">(</span>self<span class="token punctuation">)</span><span class="token punctuation">:</span>
        <span class="token keyword">import</span> users<span class="token punctuation">.</span>signals
</code></pre>
<p><a href="#signals-doc">More on Signals</a></p>
<h3 id="generic-display-views">Generic Display Views:</h3>
<p><strong><a href="https://docs.djangoproject.com/en/3.1/ref/class-based-views/generic-display/#listview">ListView</a></strong>: A page representing a list of objects.</p>
<p><strong><a href="https://docs.djangoproject.com/en/3.1/ref/class-based-views/generic-display/#detailview">DetailView</a></strong>: While this view is executing, <code>self.object</code> will contain the object that the view is operating upon.</p>
<p><strong><a href="https://docs.djangoproject.com/en/3.1/ref/class-based-views/generic-editing/#updateview">UpdateView</a></strong>: A view that displays a form for editing an existing object, redisplaying the form with validation errors (if there are any) and saving changes to the object. This uses a form automatically generated from the object’s model class (unless a form class is manually specified).</p>
<p><strong><a href="https://docs.djangoproject.com/en/3.1/ref/class-based-views/generic-editing/#createview">CreateView</a></strong>: A view that displays a form for creating an object, redisplaying the form with validation errors (if there are any) and saving the object.</p>
<p><strong><a href="https://docs.djangoproject.com/en/3.1/ref/class-based-views/generic-editing/#deleteview">DeleteView</a></strong>: A view that displays a confirmation page and deletes an existing object. The given object will only be deleted if the request method is <code>POST</code>. If this view is fetched via <code>GET</code>, it will display a confirmation page that should contain a form that POSTs to the same URL.</p>
<h3 id="documentations">Documentations:</h3>
<h4 id="data-form">Data Form:</h4>
<p><a href="https://docs.djangoproject.com/en/2.0/ref/templates/builtins/#date">time, date formating etc.</a></p>
<h4 id="serving-media">Serving Media:</h4>
<p><a href="https://docs.djangoproject.com/en/2.1/howto/static-files/#serving-files-uploaded-by-a-user-during-development">Serving files uploaded by a user during development</a></p>
<p><a href="https://docs.djangoproject.com/en/3.1/topics/db/examples/one_to_one/">One-to-One relationship in django</a></p>
<p><a href="https://docs.djangoproject.com/en/3.1/topics/db/examples/many_to_many/">Many-to-Many relationship in django</a></p>
<h4 id="signals-doc">Signals Doc</h4>
<p><a href="https://docs.djangoproject.com/en/3.1/topics/signals/">Method Definition</a><br>
<a href="https://simpleisbetterthancomplex.com/tutorial/2016/07/28/how-to-create-django-signals.html">How to create signals for profile example</a></p>

