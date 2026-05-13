---


---

<h1 id="docker-compose">Docker-Compose</h1>
<p><strong>Docker Compose solves the problem of managing multi-container applications by letting you describe the entire setup in a single <code>docker-compose.yml</code> file.</strong></p>
<p>Docker Compose introduces several essential concepts that are necessary to understand and be able to use the tool effectively. These consist of the architecture of a Docker Compose file written in YAML, services, networks, volumes, and environment variables. Lets discuss each of these concepts.</p>
<p>Key ideas from the passage:</p>
<ul>
<li><strong>One container = one responsibility</strong>
<ul>
<li>Example:
<ul>
<li>App container → runs your web app</li>
<li>Database container → runs PostgreSQL/MySQL</li>
<li>Cache container → runs Redis</li>
<li>Queue container → runs RabbitMQ</li>
</ul>
</li>
</ul>
</li>
<li><strong>Managing many <code>docker run</code> commands becomes difficult</strong>
<ul>
<li>You must manually:
<ul>
<li>create networks</li>
<li>connect containers</li>
<li>manage ports and volumes</li>
<li>clean everything up afterward</li>
</ul>
</li>
</ul>
</li>
<li><strong>Docker Compose simplifies this</strong>
<ul>
<li>You define:
<ul>
<li>services</li>
<li>networks</li>
<li>volumes</li>
<li>environment variables</li>
<li>dependencies</li>
</ul>
</li>
</ul>
</li>
</ul>
<h4 id="key-elements-of-yaml-file">Key Elements of YAML File</h4>
<ul>
<li><strong>Version</strong>  − This defines the format of the Docker Compose file so that it ensures compatibility with different Docker Compose features.</li>
<li><strong>Services</strong>  − Contains lists of all services (containers) composing the application. Each service is described with uncounted configuration options.</li>
<li><strong>Networks</strong>  − It will specify custom networks for inter-container communication and may specify the configuration options and network drivers.</li>
<li><strong>Volumes</strong>  − Declares shared volumes that are used to allow persistent storage. Volumes can be shared between services or used to store data outside the container’s lifecycle.</li>
</ul>
<p>Example:-</p>
<pre><code>version:  '3.8' 
services: web: 
image: nginx:latest 
ports:  -  "80:80" 
volumes:  - web-data:/var/www/html 
networks:  - webnet 
database: image: mysql:latest environment: MYSQL_ROOT_PASSWORD: example 
volumes:  - db-data:/var/lib/mysql 
networks:  - webnet 
networks: webnet: driver: bridge 
volumes: web-data: db-data:
</code></pre>
<h3 id="docker-compose-services">Docker Compose Services</h3>
<p>Services in Docker Compose represent the containers comprising the user’s application. Each service is defined in the <code>services</code> section of the <code>docker-compose.yml</code> file and has its configuration such as a Docker image to use, variables within the environment, ports, volumes, and network settings.</p>
<h3 id="key-service-configuration-options">Key Service Configuration Options</h3>
<p><strong>1. Image</strong></p>
<p>Specifies the Docker image used for the service.</p>
<p>Example:</p>
<pre><code>services:  web:    image: nginx:latest
</code></pre>
<p><strong>2. Build</strong></p>
<p>Instead of pulling an image, Compose can build one from a Dockerfile.</p>
<p>Example:</p>
<pre><code>services:  app:    build: .
</code></pre>
<p><strong>3. Ports</strong></p>
<p>Maps ports between the host machine and the container.</p>
<p>Syntax:</p>
<pre><code>services:  
web:  
image: nginx  
ports:  
- "8080:80"
</code></pre>
<p><strong>4. Volumes</strong></p>
<p>Volumes provide persistent storage or file sharing.</p>
<p>Example:</p>
<pre><code>services:  db:    
image: postgres    
volumes:     
	- db-data:/var/lib/postgresql/data
</code></pre>

