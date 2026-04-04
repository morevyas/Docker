---


---

<h1 id="docker">Docker</h1>
<h2 id="what-is-docker">What is Docker?</h2>
<p>Docker lets you run apps in containers.<br>
A container is like a small, portable box that has everything your app needs.</p>
<p>👉 Works the same on any machine.</p>
<hr>
<h2 id="basic-ideas">Basic Ideas</h2>
<ul>
<li><strong>Image</strong> → Blueprint of your app</li>
<li><strong>Container</strong> → Running app</li>
<li><strong>Dockerfile</strong> → Instructions to build image</li>
</ul>
<hr>
<h2 id="install-docker">Install Docker</h2>
<p>Go to: <a href="https://www.docker.com/">https://www.docker.com/</a><br>
Download Docker Desktop and install.</p>
<hr>
<h2 id="basic-commands">Basic Commands</h2>
<h3 id="check-docker">Check Docker</h3>
<pre class=" language-bash"><code class="prism  language-bash">docker --version
</code></pre>
<h3 id="download-image">Download image</h3>
<pre class=" language-bash"><code class="prism  language-bash">docker pull nginx
</code></pre>
<h3 id="run-container">Run container</h3>
<pre class=" language-bash"><code class="prism  language-bash">docker run -p 8080:80 nginx
</code></pre>
<p>Now open: <a href="http://localhost:8080">http://localhost:8080</a></p>
<hr>
<h3 id="see-running-containers">See running containers</h3>
<pre class=" language-bash"><code class="prism  language-bash">docker <span class="token function">ps</span>
</code></pre>
<h3 id="stop-container">Stop container</h3>
<pre class=" language-bash"><code class="prism  language-bash">docker stop <span class="token operator">&lt;</span>id<span class="token operator">&gt;</span>
</code></pre>
<hr>
<h2 id="simple-dockerfile">Simple Dockerfile</h2>
<pre class=" language-dockerfile"><code class="prism  language-dockerfile"><span class="token keyword">FROM</span> node<span class="token punctuation">:</span>18
<span class="token keyword">WORKDIR</span> /app
<span class="token keyword">COPY</span> . .
<span class="token keyword">RUN</span> npm install
<span class="token keyword">CMD</span> <span class="token punctuation">[</span><span class="token string">"npm"</span><span class="token punctuation">,</span> <span class="token string">"start"</span><span class="token punctuation">]</span>
</code></pre>
<hr>
<h2 id="build-image">Build image</h2>
<pre class=" language-bash"><code class="prism  language-bash">docker build -t myapp <span class="token keyword">.</span>
</code></pre>
<h2 id="run-your-app">Run your app</h2>
<pre class=" language-bash"><code class="prism  language-bash">docker run -p 3000:3000 myapp
</code></pre>
<hr>
<h2 id="docker-compose-simple">Docker Compose (Simple)</h2>
<p>Run multiple services easily.</p>
<pre class=" language-yaml"><code class="prism  language-yaml"><span class="token key atrule">version</span><span class="token punctuation">:</span> <span class="token string">'3'</span>
<span class="token key atrule">services</span><span class="token punctuation">:</span>
  <span class="token key atrule">app</span><span class="token punctuation">:</span>
    <span class="token key atrule">build</span><span class="token punctuation">:</span> .
    <span class="token key atrule">ports</span><span class="token punctuation">:</span>
      <span class="token punctuation">-</span> <span class="token string">"3000:3000"</span>
</code></pre>
<p>Run:</p>
<pre class=" language-bash"><code class="prism  language-bash">docker-compose up
</code></pre>
<hr>
<h2 id="why-use-docker">Why use Docker?</h2>
<ul>
<li>No “it works on my machine” problem</li>
<li>Easy to share apps</li>
<li>Fast setup</li>
</ul>
<hr>

