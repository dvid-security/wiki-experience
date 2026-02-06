# Docker

Docker is an open-source platform that enables developers to build, package, and deploy applications in lightweight, portable containers. These containers allow applications to run consistently across different environments, whether it's a developer’s laptop, a testing server, or a production cloud server.

Docker simplifies software deployment by bundling an application with all its dependencies, libraries, and configurations into a single container image that can run anywhere.

## Main usages

1. Microservices: Run independent services in separate containers.
2. CI/CD Pipelines: Automate application testing and deployment.
3. Cloud Deployments: Deploy scalable applications with Kubernetes.
4. Local Development: Develop in isolated environments without affecting the host system.

The containers have a good portability between systems, and permi to easily deploy multiple instances of an application. They are more efficient a rapid to deploy than classic virtual machines. Additionally, they allow to a good isolation with each container that runs in its own environment without interfering with other applications.

## How Docker works

Docker operates using three main components:

- Docker Image: A template containing an application and its dependencies. Example: `python:3.9`, `nginx:latest`
- Docker Container: A running instance of an image. Example: running an Nginx web server inside a container.
- Docker Engine: The core runtime that manages images, containers, and networks.

Here are the main differences, at a high level, between a container and a virtual machine:

| Features     | Container             | Virtual Machine        |
|--------------|-----------------------|------------------------|
| Size         | Lightweight (MBs)     | Heavy (GBs)            |
| Startup Time | Seconds               | Minutes                |
| Performance  | Near native           | Slower                 |
| Isolation    | Process level         | Full OS level          |
| Use Case     | Microservices, DevOps | Full OS virtualization |

## Command line examples

This section will present some basic commands to work with Docker.

### Install Docker

To install Docker, here are the steps depending on your operating system.

- Linux: sudo apt install docker.io
- macOS/Windows: Download from Docker’s official website.

### Check Docker version

```bash
docker --version
```

### Run a container

In this example, it is a Nginx web server.

```bash
docker run -d -p 80:80 --name my-nginx nginx
```

This command pulls the latest Nginx image, starts a container in detached mode (-d), and maps port 80 of the container to port 80 of the host.

### List running containers

```bash
docker ps
```

### Stop and remove a container

```bash
docker stop my-nginx
docker rm my-nginx
```

### Pull a specific image

This command will pull a Docker image from the official Docker registry (here, the latest Ubuntu image).

```bash
docker pull ubuntu:latest
```

To pull a custom image from a specific registry:

```bash
docker image pull myregistry.local:5000/testing/test-image
```

### Run an interactive container

This command permits to open an interactive shell inside an Ubuntu container.

```bash
docker run -it ubuntu bash
```

### Build a custom image

By using a **Dockerfile**, it is possible to create and build a custom Docker image. A Dockerfile is a simple text file, named `Dockerfile`, that contains all the instructions for Docker to create the image.

1. Create a Dockerfile for a Python application:

```
FROM python:3.9
WORKDIR /app
COPY . /app
CMD ["python", "app.py"]
```

2. Then build and run:

```bash
docker build -t my-python-app .
docker run my-python-app
```

### Remove unused images

```bash
docker system prune -a
```