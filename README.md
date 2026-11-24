# docker Practice


## Official Documentation

Use these resources for deeper learning.

| Topic | Documentation |
|---|---|
| Docker Overview | https://docs.docker.com/get-started/docker-overview/ |
| Docker Installation | https://docs.docker.com/engine/install/ |
| Docker Images | https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-an-image/ |
| Docker Containers | https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-a-container/ |
| Dockerfile | https://docs.docker.com/reference/dockerfile/ |
| Docker Compose | https://docs.docker.com/compose/ |
| Docker Volumes | https://docs.docker.com/engine/storage/volumes/ |
| Docker Networking | https://docs.docker.com/engine/network/ |
| Docker Security | https://docs.docker.com/engine/security/ |
| Docker Build | https://docs.docker.com/build/ |
| Docker Scout | https://docs.docker.com/scout/ |



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

# 7. Docker Images

### What is a Docker Image?

A Docker image is a read-only template containing everything required to create a container.

An image can include:

- Base operating system or runtime
- Application code
- Dependencies
- Configuration
- Startup instructions

### Pull an Image

```bash
docker pull nginx
```

### List Images

```bash
docker images
```

Alternative:

```bash
docker image ls
```

### Inspect an Image

```bash
docker image inspect nginx
```

### Remove an Image

```bash
docker rmi nginx
```

### Remove Unused Images

```bash
docker image prune
```

### Build an Image

```bash
docker build -t my-app .
```

Explanation:

- `docker build`: Builds an image.
- `-t`: Assigns a name and optional tag.
- `my-app`: Image name.
- `.`: Current directory is the build context.

### Image Naming Convention

```text
repository:tag
```

Example:

```text
node:22-alpine
postgres:17
nginx:latest
```

A tag identifies a particular version or variant of an image.

**Best Practice:** Avoid relying on `latest` in production. Prefer a specific, tested version.

---
