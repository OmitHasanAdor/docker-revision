# Docker: Zero to Advanced Complete Notes

A complete beginner-friendly Docker guide with explanations, commands, examples, and practical projects.

---

# Table of Contents

1. Introduction to Docker
2. Why Docker?
3. Virtual Machine vs Docker
4. Docker Architecture
5. Important Docker Terminologies
6. Docker Installation
7. Docker Hub
8. Docker Images
9. Docker Containers
10. Essential Docker Commands
11. Container Port Mapping
12. Environment Variables
13. Dockerfile
14. Docker Volumes and Bind Mounts
15. Docker Networking
16. Docker Compose
17. Dockerizing a Node.js Application
18. Dockerizing a Next.js Application
19. PostgreSQL with Docker
20. Full Stack Application with Docker Compose
21. Docker Image Layers and Caching
22. Multi-stage Builds
23. Docker Security
24. Docker Optimization
25. Docker Registry
26. Docker Deployment
27. Docker with CI/CD
28. Troubleshooting
29. Important Interview Questions
30. Official Documentation

---

# 1. Introduction to Docker

### What is Docker?

Docker is an open-source platform that allows developers to package applications and their dependencies into containers.

A container provides a consistent environment to run an application across different systems.

**Example:**

Suppose you build a Node.js application. It requires:

- Node.js
- npm packages
- Environment variables
- Application source code

Your application works on your computer but fails on another computer because of different Node.js versions or dependencies.

Docker helps solve this problem by packaging the application and its required environment into a container.

### What is Containerization?

Containerization is the process of packaging an application and its dependencies into an isolated, portable container.

### Why Docker?

- Consistent development environment.
- Easy application deployment.
- No dependency conflicts.
- Easy collaboration between developers.
- Lightweight compared to traditional virtual machines.
- Supports microservices architecture.
- Simplifies testing and CI/CD.

---

# 2. Virtual Machine vs Docker

| Virtual Machine | Docker Container |
|---|---|
| Runs a complete guest OS | Shares host OS kernel |
| Uses a hypervisor | Uses container runtime |
| Generally heavier | Generally lightweight |
| Takes more resources | Uses fewer resources |
| Usually slower to start | Usually starts quickly |
| Stronger OS-level isolation | Process-level isolation |

**Remember:**

A Virtual Machine includes a guest operating system, whereas containers share the host operating system kernel.

---

# 3. Docker Architecture

Docker follows a Client-Server architecture.

### Main Components

**1. Docker Client**

The interface used to communicate with Docker.

Example:

```bash
docker run nginx
```

**2. Docker Daemon (dockerd)**

A background service responsible for managing Docker objects such as images, containers, networks, and volumes.

**3. Docker Host**

The machine where Docker Engine runs.

**4. Docker Registry**

A storage system for Docker images.

Example: Docker Hub.

**5. Docker Objects**

- Images
- Containers
- Networks
- Volumes

### How Docker Works

```text
Docker Client
     |
     | Docker API
     |
Docker Daemon
     |
     |------------------|
     |         |        |
   Images  Containers Networks
              |
           Volumes
```

---

# 4. Important Docker Terminologies

| Term | Meaning |
|---|---|
| Docker Engine | Platform that builds and runs containers |
| Docker Image | Template used to create containers |
| Docker Container | Running or stopped instance of an image |
| Dockerfile | Instructions for building an image |
| Docker Hub | Public image registry |
| Docker Volume | Persistent storage for container data |
| Docker Network | Communication between containers |
| Docker Compose | Tool for managing multiple containers |
| Docker Registry | Image storage and distribution system |
| Docker Daemon | Background Docker service |

### Image vs Container

Think of it like this:

- Class = Image
- Object = Container

An image is a template. A container is an instance created from that template.

One image can create multiple containers.

---

# 5. Docker Installation

### Windows Installation

Requirements:

- Windows 10 or Windows 11.
- WSL 2 support.
- Hardware virtualization enabled.
- Docker Desktop.

Official installation guide:

https://docs.docker.com/desktop/setup/install/windows-install/

### Check Installation

```bash
docker --version
```

Check Docker information:

```bash
docker info
```

Check whether Docker is working:

```bash
docker run hello-world
```

This command downloads the hello-world image if necessary, creates a container, runs it, and displays a success message.

---

# 6. Docker Hub

Docker Hub is a cloud-based registry where developers can find, download, and publish Docker images.

Website: https://hub.docker.com/

### Common Docker Hub Images

- nginx
- node
- postgres
- mongo
- redis
- mysql
- ubuntu

### Pull an Image

```bash
docker pull nginx
```

This downloads the Nginx image to your local machine.

### Login to Docker Hub

```bash
docker login
```

### Logout

```bash
docker logout
```

---
