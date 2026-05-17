## Containers

A container is a lightweight, isolated environment that packages an application with everything it needs to run: code, runtime, libraries, and config. It shares the host OS kernel, so it starts fast and uses fewer resources than a virtual machine.

## Docker

Docker is a platform used to build, ship, and run containers. It lets you create consistent environments so your app behaves the same on your laptop, server, or cloud.

## Container Layers

Containers are built using **layers**. Each instruction in a Dockerfile typically adds a new layer, such as installing packages, copying files, or setting environment variables.

## Why layers matter

- Faster builds, because unchanged layers are reused from cache.
- Smaller image updates, because only changed layers are rebuilt.
- Better storage efficiency, since multiple images can share common layers.

## Key Points

- A container is not a full OS.
- Containers isolate processes, networking, and filesystem access.
- Docker images are made of read-only layers.
- A running container adds one writable layer on top of the image layers.

## Simple Example

If your Dockerfile has:
1. `FROM node:20`
2. `COPY package.json`
3. `RUN npm install`
4. `COPY .`

Then Docker builds a separate layer for each step, and if only your code changes, earlier layers like `npm install` can be reused.

## Image

A Docker image is a **read-only template** that contains the app code, runtime, libraries, and configuration needed to create a container. It is the blueprint or package used to launch one or more containers

## Comparing Image & Container

| Aspect     | Image                                       | Container                                       |
| ---------- | ------------------------------------------- | ----------------------------------------------- |
| Nature     | Static, read-only template                  | Running instance of an image                    |
| Mutability | Immutable                                   | Writable at runtime through a thin top layer    |
| Role       | Defines what will run                       | Actually runs the application                   |
| Usage      | Stored, shared, and pulled from registries  | Started, stopped, and deleted as a live process |
## Image Layers

![[Pasted image 20260518020544.png]]

So, basically all these are the bifurcation of layers being used to develop/deploy the container.


## Container Port vs Host Port Binding (Port Mapping)

## Container Port

A **container port** is the port **inside the container** that your application listens on. The container is isolated, so traffic **cannot reach** this port from outside unless you publish it.

## Host Port

A **host port** is the port **on your machine** (your computer) that receives incoming traffic. Docker forwards traffic from this port into the container's port.

## Port Binding (Port Mapping)

Binding a host port to a container port creates a **forwarding rule** so external traffic can reach your containerized app.

|Format|Meaning|
|---|---|
|`-p 8080:80`|Host port `8080` → Container port `80`|
|`-p 3000:3000`|Host port `3000` → Container port `3000` [](https://medium.com/@ppran234/why-do-we-bind-ports-in-docker-4f2a62ea2e69)|
|`-p 80`|Docker picks a random ephemeral host port automatically [](https://docs.docker.com/get-started/docker-concepts/running-containers/publishing-ports/)|
|`-p 127.0.0.1:8080:80`|Host port `8080` only accessible from localhost [](https://docs.docker.com/get-started/docker-concepts/running-containers/publishing-ports/)|


## Docker vs Virtual Machine (VM)

## What Is a VM?

A **Virtual Machine** is a **complete virtualized computer** with its own guest OS, virtualized hardware, and kernel. It runs on a hypervisor (like VirtualBox, VMware, Hyper-V).[](https://docs.docker.com/get-started/docker-concepts/running-containers/publishing-ports/)

## What Is Docker?

**Docker** uses **containers**, which are lightweight, isolated environments that share the **host OS kernel** but have isolated processes, filesystem, and networking.[](https://docs.docker.com/get-started/docker-concepts/running-containers/publishing-ports/)

## Key Differences

|Aspect|Docker (Container)|Virtual Machine|
|---|---|---|
|**OS**|Shares host OS kernel|Runs separate guest OS [](https://docs.docker.com/get-started/docker-concepts/running-containers/publishing-ports/)|
|**Size**|MBs (10–100 MB)|GBs (1–50 GB) [](https://docs.docker.com/get-started/docker-concepts/running-containers/publishing-ports/)|
|**Startup**|Seconds or less|Minutes [](https://docs.docker.com/get-started/docker-concepts/running-containers/publishing-ports/)|
|**Performance**|Near-native (no hardware virtualization)|Overhead from hypervisor [](https://docs.docker.com/get-started/docker-concepts/running-containers/publishing-ports/)|
|**Isolation**|Process-level (less isolated)|Full hardware-level (more isolated) [](https://docs.docker.com/get-started/docker-concepts/running-containers/publishing-ports/)|
|**Portability**|High (images are small, portable)|Lower (large images, OS-dependent) [](https://docs.docker.com/get-started/docker-concepts/running-containers/publishing-ports/)|
|**Resource Usage**|Low overhead|High overhead (CPU, RAM, disk) [](https://docs.docker.com/get-started/docker-concepts/running-containers/publishing-ports/)|


## When to Use Each

## Use Docker When:

- You need **fast startup** and scaling    
- You want **microservices architecture
- You need **lightweight, portable apps
- You're doing **DevOps, CI/CD, cloud-native

## Use VM When:

- You need **full OS isolation** (different OS per app)
- You're running **legacy apps** that need specific OS    
- You need **stronger security boundaries**
- You're running workloads that require **kernel-level access**

## Workflow for Dockers

![[Pasted image 20260518034927.png]]

## Commands Used

- `docker run <iamge>:version` - This directly creates the Docker Container and if there that version of Docker Container is not present locally it will `pull` or download it from DockerHub.
- `docker pull <image>:version` -  This pulls or downloads the version of that container locally.
- `docker ps` - To get information about all the running containers on the system.
- `docker run -d <image>` - This runs the Docker container in a detached mode i.e. the terminal gets freed of the buffer which Container is going to push
- `docker stop <docker-container-id>` - This stops the container running.
- `docker start <docker-container-id>` - This starts the container.
- `docker ps -a` - This gives the list of all the containers running or stopped.
- `docker run -p<host_port>:<container_port> <image>` - Now this binds the Host Port to the Container's Port
- `docker logs <NAMES>` - This give us the whole logs of what happened with the Docker Container.
- `docker run -d -p6001:6279 ==name <conatiner-name> <image>` - This gives a customized name to the Docker Container.
- `dcoker exec -it <container_id>or<container-name> /bin/bash` - This provides the shell for the Container.
- `docker network ls` - To list all the Docker Networks present
- `docker network create <network-name>` - This creates a new Docker Network
- `docker run -p 27017:27017 -e <env_var> --name <new-name> --net <network-name> <image-name>` - This creates the Docker Container with specified Environment Variables, Names and Network.
- 