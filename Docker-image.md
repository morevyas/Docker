---


---

<h1 id="docker-image">Docker image</h1>
<p>A <strong>Docker image</strong> is a <strong>lightweight, standalone, and executable software package</strong> that includes everything needed to run an application: code, runtime, system tools, libraries, and settings. It serves as a read-only blueprint for creating a docker containers.</p>
<p>Docker images are <strong>self-contained, read-only templates</strong> used to create containers. They include everything needed to run an application, such as the code, runtime, libraries, and configuration.</p>
<p>Images are built using a layered file system, where each layer represents a specific step in the build process—like installing dependencies or copying files. These layers are cached and reused, which makes image building faster and more efficient.</p>
<p>Because of this layered approach, when an image is updated, only the modified layers need to be rebuilt and transferred. This makes Docker images lightweight, efficient to share, and quick to deploy.</p>
<ul>
<li>The docker image includes the following to run a piece of software.</li>
<li>Docker images are specific to both the operating system (OS) and the CPU architecture for which they were built.</li>
</ul>
<h2 id="dockerfile">Dockerfile</h2>
<p>A <strong>Dockerfile</strong> is a simple text file that contains <strong>step-by-step instructions</strong> to build a Docker image</p>
<p>A text file known as a Dockerfile forms the basis of a Docker image. The instructions for creating the image layer by layer are contained in this file. In most cases, an instruction begins with a term such as “<strong>FROM</strong>” to identify the base image, which is usually a minimal Linux distribution. Commands such as “<strong>RUN</strong>” are then used to carry out particular operations within a layer.</p>
<p><img src="https://www.tutorialspoint.com/docker/images/docker_images_1.jpg" alt="Docker Images 1"></p>
<p>example of ubuntu image dockerfile :-</p>
<pre><code>FROM ubuntu:24.04
LABEL name="vyas"
LABEL email="vyas@gmail.com"
ENV name=vyas
ENV pass=password
RUN pwd&gt; /tmp/1stpwd.txt
WORKDIR /tmp
RUN pwd&gt;/tmp/2ndpwd.txt
RUN apt-get update &amp;&amp; apt-get install -y openssh-server
RUN useradd -d /home/$name -g root -G sudo -m -p $(openssl passwd -6 $pass) $name
RUN whoami &gt; /tmp/1stwhoami.txt
USER $name
RUN whoami &gt; /tmp/2ndwhoami.txt
RUN mkdir -p /tmp/project
ADD testproject1.tar /tmp/project
</code></pre>
<h3 id="basic-of-docker-image">Basic of docker image</h3>
<p>Docker images are read-only templates, which means any changes made while running an application occur within the container, not the image itself. This separation ensures a clear distinction between the application definition (the image) and the runtime state (the container).</p>
<p>Additionally, this design makes versioning and maintenance easier. New versions of an image can be created with specific updates without impacting existing containers, allowing applications to be updated, tested, and deployed more efficiently.</p>
<h3 id="component-of-docker-image">Component of Docker Image</h3>
<h3 id="layers">1) Layers</h3>
<p>Docker images are made up of multiple layers, where each layer represents a set of filesystem changes. During the image build process, every instruction in a Dockerfile creates a new layer on top of the previous ones.</p>
<p>These layers are immutable, meaning they cannot be changed once created. This immutability allows Docker to efficiently reuse existing layers across builds and deployments, resulting in faster build times and reduced disk space usage.</p>
<h3 id="base-image">2) Base Image</h3>
<p>A base image is the foundation on which a custom Docker image is built. It typically includes the minimal operating system and runtime environment required to run an application.</p>
<p>In a Dockerfile, the base image is specified using the <code>FROM</code> instruction, and it forms the first layer of the image. Base images can vary depending on the use case—they might be a minimal OS like <code>alpine</code>, a language runtime such as <code>python:3.9.25-slim</code>, or even a ready-to-use application like <code>nginx</code>.</p>
<p>Commonly used base images include Ubuntu, Debian, CentOS, and Alpine Linux. Choosing the right base image is important for ensuring compatibility, security, and keeping the final image size as small as possible.</p>
<h3 id="dockerfile-1">3) Dockerfile</h3>
<p>Dockerfile is a text document with a set of instructions for creating a Docker image. These instructions describe how to create the basic image, add files and directories, install dependencies, adjust settings, and define the container’s entry point.</p>
<p>By specifying the build process in a Dockerfile, you can automate and replicate the image creation process, assuring consistency across environments.</p>
<h3 id="image-registry">4) Image Registry</h3>
<p>Docker images can be stored in <strong>public or private</strong> registries such as <strong>Docker Hub, Amazon Elastic Container Registry (ECR), Google Container Registry (GCR), and Azure Container Registry (ACR)</strong>.</p>
<p>A Docker registry is a system used to <strong>store, manage, and distribute Docker images</strong>. It acts like a centralized library where users can pull official images, access community-shared images, and push their own images for reuse.</p>
<p>Docker Hub is the default public registry and the largest collection of container images. In addition to <strong>public registries, organizations often use private registries—such as Amazon ECR, Google Artifact Registry, or private Docker Hub repositories—to securely store and manage their proprietary images</strong>.</p>
<p>Registries also provide important features like image versioning, access control, and security scanning to detect vulnerabilities, making them essential for managing containerized applications efficiently.</p>
<h3 id="tagging">5) Tagging</h3>
<p>A Docker image is uniquely identified by a combination of its repository name and tag. The repository represents the image name, while the tag specifies a particular version of that image.</p>
<p>Tags are used to differentiate between different versions, such as <code>nginx:1.25</code> or <code>node:18</code>. If no tag is specified, Docker automatically uses the default tag <code>latest</code>.</p>
<p>Using meaningful tags—such as semantic versioning (<code>1.0.0</code>, <code>2.1.3</code>)—is recommended to ensure reproducibility, maintain version control, and make it easier to track changes across image versions.</p>

