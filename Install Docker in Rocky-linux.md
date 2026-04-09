---


---

<h1 id="install-docker-in-rocky-linux">Install Docker in Rocky-linux</h1>
<p>Rocky linux is  based on <strong>Red Hat Enterprise Linux (RHEL)</strong> OS</p>
<h3 id="os-requirement">OS Requirement</h3>
<p><strong>To install Docker Engine, you need a maintained version of one of the following RHEL versions</strong></p>
<ul>
<li>RHEL 8</li>
<li>RHEL 9</li>
<li>RHEL 10</li>
</ul>
<h3 id="uninstall-old-version">Uninstall old version</h3>
<p><strong>Before you can install Docker Engine, you need to uninstall any conflicting packages.</strong></p>
<p>Your Linux distribution may provide unofficial Docker packages, which may conflict with the official packages provided by Docker. You must uninstall these packages before you install the official version of Docker Engine.</p>
<p>Run this cmd</p>
<pre><code> sudo dnf remove docker \
              docker-client \
              docker-client-latest \
              docker-common \
              docker-latest \
              docker-latest-logrotate \
              docker-logrotate \
              docker-engine \
              podman \
              runc 
</code></pre>
<p><strong>Check delete or not</strong></p>
<pre><code> docker version  
</code></pre>
<h2 id="installation-method">Installation Method</h2>
<h3 id="set-up-repository.">1) Set up repository.</h3>
<pre><code>sudo dnf -y install dnf-plugins-core
sudo dnf config-manager --add-repo https://download.docker.com/linux/rhel/docker-ce.repo 
</code></pre>
<h3 id="install-the-docker-packages.">2) Install the Docker packages.</h3>
<h4 id="latest">Latest</h4>
<pre><code>sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin 
</code></pre>
<h4 id="specific-version--">Specific version :-</h4>
<pre><code>dnf list docker-ce --showduplicates | sort -r

docker-ce.x86_64    3:29.4.0-1.el9    docker-ce-stable
docker-ce.x86_64    3:29.3.1-1.el9    docker-ce-stable
&lt;...&gt;
</code></pre>
<p><strong>Select the version of install</strong></p>
<pre><code> sudo dnf install docker-ce-&lt;VERSION_STRING&gt; docker-ce-cli-&lt;VERSION_STRING&gt; containerd.io docker-buildx-plugin docker-compose-plugin  
</code></pre>
<h3 id="the-docker-service-starts-automatically-after-installation.-to-verify-that-docker-is-running.">The Docker service starts automatically after installation. To verify that Docker is running.</h3>
<p><strong>check</strong></p>
<pre><code> sudo systemctl status docker  
</code></pre>
<p><strong>Start Docker Engine.</strong></p>
<pre><code> sudo systemctl start docker  
</code></pre>
<h3 id="verify-that-the-installation-is-successful-by-running-the-hello-world-image">Verify that the installation is successful by running the <code>hello-world</code> image</h3>
<p>enter:</p>
<pre><code> sudo docker run hello-world  
</code></pre>
<h2 id="uninstall-docker-engine">Uninstall Docker Engine</h2>
<p>enter:</p>
<pre><code>sudo dnf remove docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin docker-ce-rootless-extras 
</code></pre>
<p><strong>To delete all containers, images and volumes</strong></p>
<pre><code>sudo rm -rf /var/lib/docker
</code></pre>
<p>sudo rm -rf /var/lib/containerd</p>
<p><strong>To Remove source list</strong></p>
<pre><code>sudo rm /etc/apt/sources.list.d/docker.sources  
sudo rm /etc/apt/keyrings/docker.asc  
</code></pre>
<p>check :-</p>
<pre><code>docker version
</code></pre>

