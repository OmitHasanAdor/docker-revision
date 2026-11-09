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

# 8. Docker Containers

### What is a Docker Container?

A container is an isolated runtime instance created from a Docker image.

### Create and Run a Container

```bash
docker run nginx
```

This creates and runs an Nginx container in the foreground.

### Run in Background

```bash
docker run -d nginx
```

`-d` means detached mode.

### Assign Container Name

```bash
docker run -d --name my-nginx nginx
```

### List Running Containers

```bash
docker ps
```

### List All Containers

```bash
docker ps -a
```

### Stop a Container

```bash
docker stop my-nginx
```

### Start a Stopped Container

```bash
docker start my-nginx
```

### Restart a Container

```bash
docker restart my-nginx
```

### Remove a Container

```bash
docker rm my-nginx
```

### Force Remove a Running Container

```bash
docker rm -f my-nginx
```

### View Container Logs

```bash
docker logs my-nginx
```

Follow logs continuously:

```bash
docker logs -f my-nginx
```

### Execute a Command Inside a Container

```bash
docker exec -it my-nginx sh
```

If Bash is available:

```bash
docker exec -it my-nginx bash
```

Explanation:

- `exec`: Executes a command inside an existing container.
- `-i`: Keeps standard input open.
- `-t`: Allocates a terminal.
- `sh`: Opens a shell.

Exit the container shell:

```bash
exit
```

### Inspect a Container

```bash
docker inspect my-nginx
```

### Container Resource Usage

```bash
docker stats
```

---

# 9. Essential Docker Commands

### Image Commands

```bash
docker images
docker pull nginx
docker build -t my-app .
docker rmi nginx
docker image inspect nginx
docker image prune
```

### Container Commands

```bash
docker run nginx
docker run -d nginx
docker ps
docker ps -a
docker stop container_name
docker start container_name
docker restart container_name
docker rm container_name
docker logs container_name
docker exec -it container_name sh
docker inspect container_name
docker stats
```

### System Commands

```bash
docker version
docker info
docker system df
docker system prune
docker system prune -a
```

**Important:** `docker system prune -a` removes unused containers, networks, images, and build cache. It can remove images you may want to keep. Review before running.

---

# 10. Container Port Mapping

Containers have their own network environment. To access a service inside a container from your computer, you usually need port mapping.

### Example: Run Nginx

```bash
docker run -d -p 8080:80 --name my-nginx nginx
```

Explanation:

```text
-p HOST_PORT:CONTAINER_PORT
```

Here:

- `8080` = Host port
- `80` = Container port

Now open:

```text
http://localhost:8080
```

You should see the Nginx welcome page.

### Multiple Port Mapping

```bash
docker run -d \
  -p 8080:80 \
  -p 8443:443 \
  nginx
```

---

# 11. Environment Variables

Environment variables allow applications to receive configuration values without hardcoding them into source code.

### Using -e

```bash
docker run -d \
  --name my-app \
  -e NODE_ENV=production \
  node:22-alpine
```

### Using --env-file

Create a file named `.env`:

```env
NODE_ENV=production
PORT=5000
DATABASE_URL=postgresql://user:password@db:5432/mydb
```

Run:

```bash
docker run --env-file .env my-app
```

### View Container Environment

```bash
docker exec my-app printenv
```

**Security Note:** Never commit secrets or production credentials to GitHub. Use secure secret management for production.

---

# 12. Dockerfile

### What is a Dockerfile?

A Dockerfile is a text file containing instructions that Docker uses to build an image.

It defines:

- Base image
- Working directory
- Dependencies
- Application files
- Ports
- Startup commands

### Basic Dockerfile Example

```dockerfile
FROM node:22-alpine

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 5000

CMD ["npm", "start"]
```

### Dockerfile Instructions Explained

**1. FROM**

Defines the base image.

```dockerfile
FROM node:22-alpine
```

**2. WORKDIR**

Sets the working directory inside the image.

```dockerfile
WORKDIR /app
```

**3. COPY**

Copies files from the build context into the image.

```dockerfile
COPY package*.json ./
```

**4. RUN**

Executes commands during image building.

```dockerfile
RUN npm install
```

**5. EXPOSE**

Documents which port the application is expected to listen on.

```dockerfile
EXPOSE 5000
```

It does not publish the port to the host. Use `-p` or Compose port configuration for that.

**6. CMD**

Defines the default command executed when the container starts.

```dockerfile
CMD ["npm", "start"]
```

**7. ENTRYPOINT**

Defines the main executable for the container.

```dockerfile
ENTRYPOINT ["node"]
```

**8. ENV**

Sets environment variables in the image.

```dockerfile
ENV NODE_ENV=production
```

**9. ARG**

Defines a build-time variable.

```dockerfile
ARG APP_VERSION=1.0
```

**10. ADD**

Copies files and can automatically extract local archives. Prefer `COPY` for ordinary file copying.

**11. USER**

Sets the user used to run subsequent instructions and the container process.

```dockerfile
USER node
```

**12. LABEL**

Adds metadata to an image.

```dockerfile
LABEL maintainer="developer"
```

### CMD vs RUN vs ENTRYPOINT

| Instruction | Purpose |
|---|---|
| RUN | Executes during image build |
| CMD | Provides default container startup command |
| ENTRYPOINT | Defines the main executable |
| EXPOSE | Documents the application port |

Example:

```dockerfile
FROM node:22-alpine

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

CMD ["npm", "start"]
```

### Build Docker Image

```bash
docker build -t my-node-app .
```

### Run Image

```bash
docker run -d -p 5000:5000 --name my-node-container my-node-app
```

---

# 13. .dockerignore

### What is .dockerignore?

A `.dockerignore` file tells Docker which files and directories to exclude from the build context.

This reduces unnecessary file transfers and prevents unwanted files from entering the image.

### Example

Create `.dockerignore`:

```text
node_modules
.next
.git
.env
.env.*
npm-debug.log
coverage
dist
```

**Important:** If your Dockerfile needs a particular file, do not exclude it from the build context.

---

# 14. Docker Volumes and Bind Mounts

### Why Do We Need Volumes?

Containers are designed to be replaceable. Data stored only in a container's writable layer can be lost when the container is removed.

Volumes provide persistent storage outside the container's writable layer.

### Types of Storage

1. Volumes
2. Bind Mounts
3. tmpfs Mounts

### A. Docker Volume

Docker manages the storage location.

Create a volume:

```bash
docker volume create my-volume
```

List volumes:

```bash
docker volume ls
```

Inspect volume:

```bash
docker volume inspect my-volume
```

Use volume:

```bash
docker run -d \
  --name my-nginx \
  -v my-volume:/data \
  nginx
```

Remove volume:

```bash
docker volume rm my-volume
```

### B. Bind Mount

Bind mounts connect a specific host directory to a container directory.

Example:

```bash
docker run -d \
  --name my-app \
  -v "D:/projects/my-app:/app" \
  node:22-alpine
```

Here:

- Host path: `D:/projects/my-app`
- Container path: `/app`

Changes in the host directory are reflected inside the container.

### C. Read-only Mount

```bash
docker run -d \
  -v "D:/projects/my-app:/app:ro" \
  nginx
```

`ro` means read-only.

### Volume vs Bind Mount

| Volume | Bind Mount |
|---|---|
| Managed by Docker | Uses a specific host path |
| Good for persistent application data | Good for source code sharing |
| Docker controls its location | Developer chooses its location |
| Useful for databases | Useful for development |

### Caution

Avoid mounting your complete project directory over a container directory that already contains installed dependencies unless you intentionally manage those dependencies separately.

---

# 15. Docker Networking

### What is Docker Networking?

Docker networking allows containers to communicate with one another and with external networks.

### Common Network Drivers

| Driver | Purpose |
|---|---|
| bridge | Default networking for standalone containers |
| host | Uses host networking |
| none | Disables normal container networking |
| overlay | Connects containers across Docker hosts |
| macvlan | Assigns containers MAC addresses on a network |

### List Networks

```bash
docker network ls
```

### Create Network

```bash
docker network create my-network
```

### Inspect Network

```bash
docker network inspect my-network
```

### Connect Container to Network

```bash
docker network connect my-network my-container
```

### Disconnect Container

```bash
docker network disconnect my-network my-container
```

### Remove Network

```bash
docker network rm my-network
```

### Container-to-Container Communication

Suppose you have:

- Backend container
- PostgreSQL container

Both are connected to the same user-defined Docker network.

The backend can connect to PostgreSQL using the database container's name.

```env
DATABASE_URL=postgresql://postgres:password@db:5432/mydb
```

Here, `db` is the database container's network name or network alias.

**Important:** Inside a container, `localhost` refers to that same container, not another container.

---

# 16. Docker Compose

### What is Docker Compose?

Docker Compose is a tool for defining and managing multi-container applications using a YAML configuration file.

Instead of running multiple `docker run` commands, you can define the entire application in one `compose.yaml` file.

### Why Docker Compose?

Imagine your application requires:

- Backend
- Frontend
- PostgreSQL
- Redis

Docker Compose allows you to manage all these services together.

### Basic compose.yaml

```yaml
services:
  app:
    image: nginx
    ports:
      - "8080:80"
```

Run:

```bash
docker compose up
```

Run in background:

```bash
docker compose up -d
```

Stop and remove Compose resources:

```bash
docker compose down
```

### Important Docker Compose Commands

```bash
# Start services
docker compose up

# Start in detached mode
docker compose up -d

# Build and start
docker compose up --build

# Stop services
docker compose stop

# Start stopped services
docker compose start

# Stop and remove containers and default network
docker compose down

# Remove containers, networks and named volumes declared in the Compose file
docker compose down -v

# View running services
docker compose ps

# View logs
docker compose logs

# Follow logs
docker compose logs -f

# View a specific service's logs
docker compose logs -f backend

# Execute command inside a service
docker compose exec backend sh

# Rebuild images
docker compose build

# Restart services
docker compose restart
```

### Important Compose Properties

| Property | Purpose |
|---|---|
| services | Defines application services |
| image | Uses an existing image |
| build | Builds an image from a Dockerfile |
| ports | Publishes container ports |
| volumes | Mounts storage |
| environment | Defines environment variables |
| env_file | Loads variables from a file |
| networks | Configures service networks |
| depends_on | Controls service startup order |
| restart | Defines restart policy |
| command | Overrides the default command |
| healthcheck | Checks service health |

### depends_on

```yaml
services:
  backend:
    depends_on:
      - db
```

This controls startup order, but does not automatically guarantee that the database is ready to accept connections.

For readiness, use health checks and `condition: service_healthy`.

---

# 17. Dockerizing a Node.js Application

Suppose your project structure is:

```text
my-node-app/
│
├── src/
├── package.json
├── package-lock.json
├── .env
├── .dockerignore
└── Dockerfile
```

### Step 1: Create Dockerfile

```dockerfile
FROM node:22-alpine

WORKDIR /app

COPY package*.json ./

RUN npm ci

COPY . .

EXPOSE 5000

CMD ["npm", "start"]
```

### Step 2: Create .dockerignore

```text
node_modules
.git
.env
coverage
npm-debug.log
```

### Step 3: Build Image

```bash
docker build -t my-node-app .
```

### Step 4: Run Container

```bash
docker run -d \
  --name my-node-container \
  -p 5000:5000 \
  --env-file .env \
  my-node-app
```

### Step 5: Check Logs

```bash
docker logs my-node-container
```

### Step 6: Test Application

```text
http://localhost:5000
```

---

# 18. Dockerizing a Next.js Application

Next.js applications can be deployed using Docker.

A production-friendly approach is to use Next.js standalone output and a multi-stage Docker build.

### Step 1: Update next.config.ts

```typescript
import type { NextConfig } from "next";

const nextConfig: NextConfig = {
  output: "standalone",
};

export default nextConfig;
```

### Step 2: Create Dockerfile

```dockerfile
FROM node:22-alpine AS base

WORKDIR /app

FROM base AS deps

COPY package.json package-lock.json ./

RUN npm ci

FROM base AS builder

COPY --from=deps /app/node_modules ./node_modules
COPY . .

RUN npm run build

FROM base AS runner

ENV NODE_ENV=production

WORKDIR /app

COPY --from=builder /app/public ./public
COPY --from=builder /app/.next/standalone ./
COPY --from=builder /app/.next/static ./.next/static

EXPOSE 3000

CMD ["node", "server.js"]
```

### Step 3: Build Image

```bash
docker build -t my-next-app .
```

### Step 4: Run Container

```bash
docker run -d \
  --name next-container \
  -p 3000:3000 \
  my-next-app
```

Open:

```text
http://localhost:3000
```

**Note:** If your project does not contain a `public` directory, adjust the Dockerfile accordingly. Native dependencies and platform-specific packages may also require additional configuration.

---
