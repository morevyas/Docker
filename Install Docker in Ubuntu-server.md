---


---

<h1 id="install-docker-in-ubuntu-server">Install Docker in Ubuntu-server</h1>
<h3 id="os-requirement">OS Requirement</h3>
<p><strong>To install Docker Engine, you need the 64-bit version of one of these Ubuntu versions</strong></p>
<ul>
<li>Ubuntu Resolute 26.04 (LTS)</li>
<li>Ubuntu Questing 25.10</li>
<li>Ubuntu Noble 24.04 (LTS)</li>
<li>Ubuntu Jammy 22.04 (LTS)</li>
</ul>
<p>Docker Engine for Ubuntu is compatible with <strong>x86_64 (or amd64), armhf, arm64, s390x, and ppc64le (ppc64el) architectures</strong>.</p>
<h3 id="uninstall-old-version">Uninstall old version</h3>
<p>Your Linux distribution may provide unofficial Docker packages, which may conflict with the official packages provided by Docker. You must uninstall these packages before you install the official version of Docker Engine.</p>
<p>Run this cmd</p>
<pre><code>sudo apt remove $(dpkg --get-selections docker.io docker-compose docker-compose-v2 docker-doc podman-docker containerd runc | cut -f1)
</code></pre>
<p><strong>Check delete or not</strong></p>
<pre><code>docker version
</code></pre>
<h2 id="installation-method">Installation Method</h2>
<h3 id="set-up-dockers-apt-repository.">1) Set up Docker’s <code>apt</code> repository.</h3>
<pre><code>#Add Docker's official GPG key:
sudo apt update
sudo apt install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL 
https://download.docker.com/linux/ubuntu/gpg -o 	
/etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

#Add the repository to Apt sources:
sudo tee /etc/apt/sources.list.d/docker.sources &lt;&lt;EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release &amp;&amp; echo 	
"${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Architectures: $(dpkg --print-architecture)
Signed-By: /etc/apt/keyrings/docker.asc
EOF

sudo apt update
</code></pre>
<h3 id="install-the-docker-packages.">2) Install the Docker packages.</h3>
<h4 id="latest">Latest</h4>
<pre><code>sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
</code></pre>
<h4 id="specific-version">Specific version</h4>
<pre><code>#apt list --all-versions docker-ce

docker-ce/noble 5:29.4.0-1~ubuntu.24.04~noble &lt;arch&gt;
docker-ce/noble 5:29.3.1-1~ubuntu.24.04~noble &lt;arch&gt;
...
</code></pre>
<p><strong>install</strong></p>
<pre><code>VERSION_STRING=5:29.4.0-1~ubuntu.24.04~noble
sudo apt install docker-ce=$VERSION_STRING docker-ce-	
cli=$VERSION_STRING containerd.io docker-buildx-plugin 	
docker-compose-plugin
</code></pre>
<h3 id="the-docker-service-starts-automatically-after-installation.-to-verify-that-docker-is-running.">The Docker service starts automatically after installation. To verify that Docker is running.</h3>
<p><strong>check</strong></p>
<pre><code>sudo systemctl status docker
</code></pre>
<p><strong>not running</strong></p>
<pre><code>sudo systemctl start docker
</code></pre>
<h3 id="verify-that-the-installation-is-successful-by-running-the-hello-world-image">Verify that the installation is successful by running the <code>hello-world</code> image</h3>
<p>enter:</p>
<pre><code> sudo docker run hello-world
</code></pre>
<h2 id="uninstall-docker-engine">Uninstall Docker Engine</h2>
<p>enter:</p>
<pre><code>sudo apt purge docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin docker-ce-rootless-extras
</code></pre>
<p><strong>To delete all containers, images and volumes</strong></p>
<pre><code>sudo rm -rf /var/lib/docker
sudo rm -rf /var/lib/containerd
</code></pre>
<p><strong>To Remove source list</strong></p>
<pre><code>sudo rm /etc/apt/sources.list.d/docker.sources
sudo rm /etc/apt/keyrings/docker.asc
</code></pre>

