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

## Commands Used

- `docker run <iamge>:version` - This directly runs the Docker Container and if there that version of Docker Container is not present locally it will `pull` or download it from DockerHub.
- `docker pull <image>:version` -  This pulls or downloads the version of that container locally.
- `docker ps` - To get information about all the running containers on the system.
- `docker run -d <image>` - This runs the Docker container in a detached mode i.e. the terminal gets freed of the buffer which Container is going to push
- 