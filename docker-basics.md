# 🐳 Docker Basics — From Zero to Production

![Docker](https://img.shields.io/badge/Docker-Ready-blue)
![Beginner Friendly](https://img.shields.io/badge/Beginner-Friendly-brightgreen)
![DevOps](https://img.shields.io/badge/DevOps-Path-orange)
![File](https://img.shields.io/badge/docker--basics-This%20File-purple)
![License](https://img.shields.io/badge/License-MIT-green)


> **Who is this for?**
> Total beginners who want to learn Docker step-by-step AND prepare for DevOps interviews — all in one place.
> Junior Devs, DevOps beginners, and Cloud learners.

---

## 📌 Quick Navigation

> Jump to what you need.

| What you want | Jump here |
|---------------|-----------|
| "What even is Docker?" | [What is Docker](#1-what-is-docker) |
| Core terms (Image, Container, etc.) | [Core Concepts](#3-core-concepts) |
| Run your first container | [Beginner Practice](#7-hands-on-practice) |
| The 5 Pillars of Docker | [Core Ecosystem](#9-docker-core-ecosystem--the-5-pillars) |
| Deploy & push to Docker Hub | [Flask + Registry](#10-hands-on-practice--deploy--push-to-registry) |
| Interview Q&A (all 18) | [Interview Prep](#8-interview-prep--questions--answers) |

> 💡 Use **Ctrl + F** to search anything on this page. Each section has a **[↑ Back to top](#-docker-basics--from-zero-to-production)** link at the bottom.

---

> 📌 **How to read this file:**
> - No tag = **Beginner** — start here
> - `[ADV]` = **Advanced** — come back to these after you're comfortable with the basics

---

## 1. What is Docker?

Docker is a **containerization tool** that lets you package your application **+ all its dependencies** into a single unit called a **container**.

That container runs **the same way on every machine** — your laptop, a test server, or a cloud server.

> 💡 **Simple version:** Docker solves the *"It works on my machine"* problem.

[↑ Back to top](#-docker-basics--from-zero-to-production)

---

## 2. Why Docker? (The Real Problem)

**Before Docker — what used to happen:**

| Step | Result |
|------|--------|
| Developer builds the app | ✅ Works on their laptop |
| Pushed to testing server | ❌ Crashes — different OS |
| Pushed to production | ❌ Crashes again — different library versions |

**Why it crashed:** Different operating systems, different library / software versions, different configuration settings.

**After Docker:**

Everything is packaged together → the app runs **the same everywhere**. No more environment mismatches.

[↑ Back to top](#-docker-basics--from-zero-to-production)

---

## 3. Core Concepts

These are the **building blocks** of Docker. Learn these first.

| Term | What It Means | Simple Analogy |
|------|---------------|----------------|
| **Image** | A blueprint / template for a container | A recipe |
| **Container** | A running instance built from an image | A dish made from the recipe |
| **Dockerfile** | A script with instructions to build an image | The written recipe steps |
| **Registry** | A place to store and share images (e.g., Docker Hub) | A cookbook library |
| **Volume** | Saves data so it's not lost when a container stops | A USB drive plugged into the container |

> 📌 **Remember:** Image = blueprint. Container = the running thing.

<details>
<summary><b>[ADV] Orchestration — what is it and when do you need it?</b></summary>

When you have **many containers** running together, you need a tool to manage them. This is called **orchestration**.

- **Kubernetes** — the industry standard for orchestrating containers at scale
- **Docker Swarm** — Docker's built-in (simpler) orchestration tool

> 📌 You don't need to know orchestration to start. Come back to this after you're comfortable with single containers.

</details>

[↑ Back to top](#-docker-basics--from-zero-to-production)

---

## 4. Advantages & Disadvantages

### ✅ Advantages

| Advantage | Why It Matters |
|-----------|----------------|
| **Portability** | Run your app anywhere — laptop, server, cloud |
| **Lightweight** | Uses way less memory and CPU than virtual machines |
| **Fast** | Containers start in seconds (VMs take minutes) |
| **Isolation** | Each app runs in its own space — no conflicts |
| **CI/CD Friendly** | Perfect for automated testing and deployment pipelines |
| **Easy Scaling** | Need more power? Run more copies of your container |

### ❌ Disadvantages

| Disadvantage | Why It Matters |
|--------------|----------------|
| Needs Linux kernel features | Doesn't run natively on older Windows/Mac without extra setup |
| Security risk if misconfigured | Always use trusted, verified images |
| Data is lost when container stops | You must use **Volumes** to save data |
| Learning curve | Networking and storage take time to understand |
| Not for full OS simulation | If you need a full operating system, use a VM instead |

<details>
<summary><b>[ADV] Performance vs. Bare Metal</b></summary>

Containers add a **small performance overhead** compared to running software directly on the machine (called "bare metal"). For most apps this is negligible, but for high-performance computing or GPU workloads, this trade-off matters.

</details>

[↑ Back to top](#-docker-basics--from-zero-to-production)

---

## 5. Alternatives to Docker

Docker isn't the only option. Here's what else exists and **when to use it:**

| Tool | Best For |
|------|----------|
| **Virtual Machines (VMware, VirtualBox)** | When you need a full, isolated operating system |
| **Podman** | A Docker alternative that doesn't need a background daemon — great for security-focused setups |
| **LXC / LXD** | System-level containers — closer to a lightweight VM |
| **Kubernetes (with CRI-O or containerd)** | When you're managing hundreds of containers in production |

<details>
<summary><b>[ADV] rkt (CoreOS) — deprecated</b></summary>

**rkt** was a security-focused container runtime made by CoreOS. It has been **deprecated** (no longer maintained). Kubernetes with CRI-O fills the same role today.

</details>

[↑ Back to top](#-docker-basics--from-zero-to-production)

---

## 6. Real-World Use Cases

Docker is used by companies like **Netflix, Amazon, and Google** every single day.

| Use Case | What Happens |
|----------|--------------|
| **Microservices** | Each small service (login, payments, search) runs in its own container |
| **CI/CD Pipelines** | Code is automatically tested and deployed using containers (e.g., Jenkins + Docker) |
| **Cloud Deployment** | Apps are deployed to AWS, Azure, or GCP inside containers |
| **Testing Environments** | Every developer gets an identical test environment — no "works on my machine" |
| **Running Databases Safely** | Databases run in containers so they're isolated and easy to manage |
| **Team Dev Environments** | New team member? Just run one command and their environment is ready |

<details>
<summary><b>[ADV] Cloud Deployment Services — which provider uses what</b></summary>

| Cloud Provider | Container Service |
|----------------|-------------------|
| AWS | ECS (Elastic Container Service), EKS (Elastic Kubernetes Service) |
| Azure | AKS (Azure Kubernetes Service) |
| Google Cloud | GKE (Google Kubernetes Engine) |
| Oracle Cloud | OCI Container Engine |

</details>

<details>
<summary><b>[ADV] Legacy Modernization — running old apps in containers</b></summary>

Companies with **old applications** (written 10–20 years ago) wrap them inside Docker containers. This lets the old app run on modern cloud infrastructure **without rewriting the entire codebase**.

</details>

[↑ Back to top](#-docker-basics--from-zero-to-production)

---

## 7. Hands-On Practice

### 🎯 Beginner Task — Run a Python App in Docker

**Goal:** Build and run a simple Python app inside a container.

---

**Step 1: Create your app file**

Create a file called `app.py`:

```python
print("Hello from Docker! 🐳")
```

**Step 2: Create your Dockerfile**

Create a file called `Dockerfile` (no extension) in the same folder:

```dockerfile
FROM python:3.9
WORKDIR /app
COPY app.py .
CMD ["python", "app.py"]
```

**What each line does:**

| Line | Meaning |
|------|---------|
| `FROM python:3.9` | Start with an official Python image |
| `WORKDIR /app` | Set the working folder inside the container |
| `COPY app.py .` | Copy your file into the container |
| `CMD ["python", "app.py"]` | Run the app when the container starts |

**Step 3: Build the image**

```bash
docker build -t my-python-app .
```

This creates an **image** called `my-python-app`.

**Step 4: Run the container**

```bash
docker run my-python-app
```

**Output:**

```
Hello from Docker! 🐳
```

🎉 **You just ran your first container!**

---

<details>
<summary><b>[ADV] Intermediate Task — Run a Node.js Web Server</b></summary>

**Goal:** Run a real web app that you can open in your browser.

**Step 1: Create `package.json`**

```json
{
  "name": "docker-node-app",
  "version": "1.0.0",
  "dependencies": {
    "express": "^4.18.2"
  },
  "scripts": {
    "start": "node index.js"
  }
}
```

**Step 2: Create `index.js`**

```javascript
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('<h1>Hello from Docker + Node.js! 🐳</h1>');
});

app.listen(3000, () => {
  console.log('Server running on port 3000');
});
```

**Step 3: Create `Dockerfile`**

```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["npm", "start"]
```

**Step 4: Build & Run**

```bash
docker build -t my-node-app .
docker run -p 3000:3000 my-node-app
```

**Step 5:** Open your browser → `http://localhost:3000`

> 📌 **`-p 3000:3000`** means: connect port 3000 on **your machine** to port 3000 **inside the container**. This is called **port mapping**.

</details>

<details>
<summary><b>[ADV] Key Docker Commands — Cheat Sheet</b></summary>

| Command | What It Does |
|---------|--------------|
| `docker build -t name .` | Build an image from a Dockerfile |
| `docker run image_name` | Run a container |
| `docker run -p 8080:80 image` | Run with port mapping |
| `docker ps` | See all running containers |
| `docker ps -a` | See ALL containers (including stopped) |
| `docker stop container_id` | Stop a container |
| `docker rm container_id` | Remove a stopped container |
| `docker images` | See all images on your machine |
| `docker logs container_id` | See the output/logs of a container |
| `docker inspect container_id` | Get detailed info about a container |

</details>

[↑ Back to top](#-docker-basics--from-zero-to-production)

---

## 8. Interview Prep — Questions & Answers

These are **real questions** asked in DevOps interviews. Read the question first, try to answer yourself, then reveal.

---

### 🟢 Beginner Level

<details>
<summary><b>Q1: What is Docker and what problem does it solve?</b></summary>

Docker is a containerization platform that packages an application and all its dependencies into a portable unit called a container. It solves the **"It works on my machine"** problem by ensuring the app runs identically across all environments — development, testing, and production.

</details>

<details>
<summary><b>Q2: What is the difference between a Docker Image and a Docker Container?</b></summary>

- **Image** = A read-only **template/blueprint**. Think of it as a recipe.
- **Container** = A **running instance** created from an image. Think of it as the dish made from the recipe.

You can create **multiple containers** from a single image.

</details>

<details>
<summary><b>Q3: What is a Dockerfile?</b></summary>

A Dockerfile is a **text file with step-by-step instructions** that Docker uses to automatically build an image. Each line is a command (like `FROM`, `COPY`, `RUN`, `CMD`).

</details>

<details>
<summary><b>Q4: How is Docker different from a Virtual Machine (VM)?</b></summary>

| Feature | Docker Container | Virtual Machine |
|---------|-----------------|-----------------|
| **Uses** | Shared host OS kernel | Its own full OS |
| **Size** | Very small (MBs) | Large (GBs) |
| **Startup time** | Seconds | Minutes |
| **Resource usage** | Lightweight | Heavy |
| **Isolation level** | Process-level | Full OS-level |

> **Short answer for interviews:** Containers share the host OS kernel and are lightweight. VMs run a full operating system and are heavier.

</details>

---

### 🟡 Intermediate Level

<details>
<summary><b>Q5: What is a Docker Registry and name an example?</b></summary>

A Docker Registry is a **storage server** where Docker images are kept and shared. The most popular one is **Docker Hub** (hub.docker.com). Companies can also run private registries (e.g., AWS ECR, GitLab Registry).

</details>

<details>
<summary><b>Q6: What is a Docker Volume and why do we need it?</b></summary>

By default, **data inside a container is lost** when the container stops. A **Volume** is a way to store data **outside** the container so it persists even after the container is deleted.

```bash
docker run -v /host/path:/container/path my-app
```

This maps a folder on your machine to a folder inside the container.

</details>

<details>
<summary><b>Q7: Your containerized app works locally but crashes in production. How do you troubleshoot?</b></summary>

Step-by-step troubleshooting:

1. **Check logs** → `docker logs container_id`
2. **Check environment variables** → Make sure all config values are set correctly in production
3. **Inspect the container** → `docker inspect container_id`
4. **Verify networking** → Is the app trying to reach a service that isn't available in production?
5. **Compare images** → Make sure the same image version is running locally and in production
6. **Check resource limits** → Production might have memory/CPU limits the container needs

</details>

---

### 🔴 Advanced Level

<details>
<summary><b>Q8: What is the difference between Docker Compose and Kubernetes?</b></summary>

| Feature | Docker Compose | Kubernetes |
|---------|---------------|------------|
| **Purpose** | Run multiple containers on **one machine** | Manage containers across **many machines** |
| **Scale** | Small to medium apps | Large-scale, enterprise apps |
| **Complexity** | Simple (one YAML file) | Complex but very powerful |
| **Use case** | Local development, small deployments | Production cloud deployments |

</details>

<details>
<summary><b>Q9: What is a Docker layer and how does caching work?</b></summary>

Every line in a Dockerfile creates a **layer**. Docker **caches** each layer. When you rebuild an image, Docker only rebuilds the layers that **changed** — everything above is reused from cache.

**Best practice:** Put things that change rarely (like `npm install`) **before** things that change often (like your app code). This makes builds faster.

```dockerfile
# ✅ Good order — npm install is cached unless package.json changes
COPY package*.json ./
RUN npm install
COPY . .            # Only this layer rebuilds when code changes
```

</details>

<details>
<summary><b>Q10: How do containers communicate with each other?</b></summary>

Containers communicate using **Docker Networks**:

- **Bridge Network** (default) — Containers on the same network can talk to each other using container names
- **Host Network** — Container shares the host machine's network directly
- **None Network** — Container has no network access (fully isolated)

In **Docker Compose**, all containers in the same `docker-compose.yml` are automatically on the same network.

</details>

[↑ Back to top](#-docker-basics--from-zero-to-production)

---

## 9. Docker Core Ecosystem — The 5 Pillars

Every Docker workflow is built on **5 key concepts**. Once you understand how they connect, interviews become easy.

> 💡 **The full flow in one line:**
> `Dockerfile → Image → Registry → Container → Orchestration`

---

<details>
<summary><b>9.1 Docker Image — the blueprint</b></summary>

**What it is:** An immutable snapshot that contains everything your app needs to run — the OS layer, app code, libraries, and dependencies.

> 📌 **Think of it as:** A CD/DVD. You can read it, copy it, and share it — but you can't change what's on it.

**Why it matters:**
Everyone on your team pulls the **exact same image** → everyone runs the **exact same app**. No version conflicts.

**How it's used in the real world:**

| Who | What They Do |
|-----|--------------|
| Developer | Builds a custom image for their microservice |
| CI/CD Pipeline | Automatically builds a fresh image on every code push |
| Production Server | Pulls the image and runs it as a container |

---

**[ADV] Image Optimization**

Images can grow **very large** if you're not careful. Two rules to keep them small:

- Use **slim / alpine** base images (e.g., `python:3.11-slim` instead of `python:3.11`)
- Use **multi-stage builds** — build in one stage, copy only the final output into a tiny image

```dockerfile
# Stage 1 — build
FROM node:18 AS builder
WORKDIR /app
COPY . .
RUN npm install && npm run build

# Stage 2 — final image (tiny)
FROM node:18-alpine
COPY --from=builder /app/dist /app/dist
CMD ["node", "/app/dist/index.js"]
```

> 📌 The final image only contains the built output — not `node_modules`, not source code. Much smaller.

</details>

---

<details>
<summary><b>9.2 Docker Container — the running instance</b></summary>

**What it is:** A running instance created from an image. It's isolated, lightweight, and fast.

> 📌 **Think of it as:** Image = class → Container = object. One image can create many containers.

**Why it matters:**
Each container runs in its **own space**. Containers don't interfere with each other — even if they're on the same machine.

**Quick command:**

```bash
docker run nginx
```

This pulls the `nginx` image (if not already downloaded) and starts a container from it.

---

**[ADV] Container Lifecycle**

A container goes through these stages:

| Stage | What's Happening |
|-------|-----------------|
| **Created** | Container is built from an image but not started yet |
| **Running** | Container is active and executing |
| **Paused** | Container is temporarily frozen |
| **Stopped** | Container has finished or been stopped |
| **Removed** | Container is deleted from the system |

```bash
docker create nginx          # Created
docker start container_id    # Running
docker pause container_id    # Paused
docker stop container_id     # Stopped
docker rm container_id       # Removed
```

---

**[ADV] Container vs. Image — Pros & Cons**

| Concept | Pros | Cons |
|---------|------|------|
| **Image** | Portable, reproducible, shareable | Can grow large if not optimized |
| **Container** | Lightweight, fast startup | Limited isolation compared to VMs |

</details>

---

<details>
<summary><b>9.3 Dockerfile — the recipe</b></summary>

**What it is:** A simple text file with step-by-step instructions that Docker reads to **automatically build an image**.

> 📌 **Think of it as:** A recipe. Docker follows each line, top to bottom, and builds your image.

**Example — a real Dockerfile broken down:**

```dockerfile
FROM python:3.11-slim        # Start from an official Python image
WORKDIR /app                 # Set the working folder
COPY requirements.txt .      # Copy the requirements file first
RUN pip install -r requirements.txt   # Install all dependencies
COPY . .                     # Copy all your app code
EXPOSE 5000                  # Tell Docker which port the app uses
CMD ["python", "app.py"]     # Run the app when container starts
```

**What each line does:**

| Line | Meaning |
|------|---------|
| `FROM python:3.11-slim` | Use Python 3.11 slim as the base (small size) |
| `WORKDIR /app` | All commands after this run inside `/app` |
| `COPY requirements.txt .` | Copy requirements **before** the rest of the code |
| `RUN pip install ...` | Install dependencies (this layer gets cached) |
| `COPY . .` | Copy your actual app code |
| `EXPOSE 5000` | Documents that port 5000 is used (doesn't actually open it — `-p` does that) |
| `CMD ["python", "app.py"]` | The default command when the container starts |

> 📌 **Why copy `requirements.txt` first?** Because Docker caches each step. If only your code changes (not your dependencies), Docker skips the `pip install` step — making builds **much faster**.

---

**[ADV] Dockerfile — Common Mistakes**

| ❌ Mistake | ✅ Fix |
|-----------|--------|
| Putting `COPY . .` before `RUN install` | Put install steps first so they get cached |
| Using a large base image like `python:3.11` | Use `python:3.11-slim` or `-alpine` |
| Running everything as root | Add `USER appuser` to run as a non-root user |
| Not using `.dockerignore` | Create a `.dockerignore` file to skip `node_modules`, `.git`, etc. |

</details>

---

<details>
<summary><b>9.4 Docker Registry — the storage</b></summary>

**What it is:** A central place to **store, share, and pull** Docker images. Think of it as GitHub — but for images.

> 📌 **The flow:** Build image → Push to Registry → Any server can Pull it → Run as Container

**Popular Registries:**

| Registry | Who It's For |
|----------|--------------|
| **Docker Hub** | Everyone — free, public, the most popular |
| **AWS ECR** | Teams using Amazon Web Services |
| **Azure ACR** | Teams using Microsoft Azure |
| **GitHub Container Registry** | Teams already using GitHub |

---

**[ADV] Public vs. Private Registries**

| Type | What It Means | Risk |
|------|---------------|------|
| **Public** (e.g., Docker Hub) | Anyone can see and pull your images | Someone could pull an unvetted image |
| **Private** (e.g., AWS ECR, Harbor) | Only your team can access images | More secure — used by enterprises |

> 📌 **Interview tip:** Always mention that enterprises use **private registries** for security. Public registries can contain images with vulnerabilities.

---

**[ADV] Registry Alternatives**

| Tool | What Makes It Different |
|------|------------------------|
| **Harbor** | Open-source, enterprise-grade private registry |
| **GitHub Container Registry** | Built into GitHub — easy if you already use GitHub |
| **GitLab Container Registry** | Built into GitLab |

</details>

---

<details>
<summary><b>9.5 Container Orchestration — the manager</b></summary>

**What it is:** When you have **many containers** running, orchestration is the system that manages them automatically.

> 📌 **Think of it as:** A traffic controller for containers. It decides where they run, keeps them healthy, and scales them up or down.

**What orchestration does:**

| Job | What It Means |
|-----|---------------|
| **Auto-scaling** | Runs more containers when traffic is high, fewer when it's low |
| **Load balancing** | Spreads incoming requests across multiple containers evenly |
| **Self-healing** | If a container crashes, it automatically restarts it |
| **Rolling updates** | Updates your app one container at a time — no downtime |

**Popular orchestration tools:**

| Tool | When to Use It |
|------|----------------|
| **Kubernetes** | The industry standard — used by Google, Netflix, Amazon |
| **Docker Swarm** | Simple clustering — good for small teams |
| **AWS ECS** | If you're already on AWS and want managed containers |

---

**[ADV] Orchestration Alternatives**

| Tool | What Makes It Different |
|------|------------------------|
| **Nomad (HashiCorp)** | Simpler than Kubernetes — works for containers AND non-container workloads |
| **OpenShift (Red Hat)** | Enterprise Kubernetes — comes with extra tooling and support |

---

**[ADV] Orchestration — Pros & Cons**

| Pros | Cons |
|------|------|
| Scales apps automatically | Steep learning curve (especially Kubernetes) |
| Self-heals — restarts crashed containers | Complex to set up and maintain |
| Handles load balancing for you | Requires networking knowledge |
| Supports rolling updates (zero downtime) | Overkill for small, single-container apps |

</details>

---

### 🧠 The Full Picture — How It All Connects

Here's how all 5 concepts work together in a **real company:**

```
Developer writes code
        ↓
  Dockerfile  ←  instructions
        ↓
  docker build  →  Image  ←  the snapshot
        ↓
  docker push  →  Registry  ←  storage
        ↓
  docker pull  →  Server pulls the image
        ↓
  Container  ←  the app is running!
        ↓
  Orchestration  ←  Kubernetes manages everything
        ↓
  Users see the app ✅
```

> 📌 **This is the exact flow DevOps interviews test.** Know this, and you're ahead of most candidates.

[↑ Back to top](#-docker-basics--from-zero-to-production)

---

## 10. Hands-On Practice — Deploy & Push to Registry

### 🎯 Intermediate Task — Flask App + Docker Hub

**Goal:** Build a Python Flask app, run it locally, then push the image to Docker Hub.

---

**Step 1: Create `requirements.txt`**

```
flask
```

**Step 2: Create `app.py`**

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def home():
    return '<h1>Hello from Flask + Docker! 🐳</h1>'

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
```

> 📌 **`host='0.0.0.0'`** is important — it tells Flask to accept connections from **outside** the container, not just localhost.

**Step 3: Create `Dockerfile`**

```dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
EXPOSE 5000
CMD ["python", "app.py"]
```

**Step 4: Build the image**

```bash
docker build -t flask-app .
```

**Step 5: Run it locally**

```bash
docker run -p 5000:5000 flask-app
```

Open your browser → `http://localhost:5000`

You should see: **Hello from Flask + Docker! 🐳**

---

<details>
<summary><b>[ADV] Step 6: Push to Docker Hub</b></summary>

First, log in to Docker Hub (create a free account at hub.docker.com):

```bash
docker login
```

Tag your image with your Docker Hub username:

```bash
docker tag flask-app your-username/flask-app:v1
```

Push it:

```bash
docker push your-username/flask-app:v1
```

**What just happened:**

| Command | What It Did |
|---------|-------------|
| `docker tag` | Gave your image a name that matches your Docker Hub account |
| `docker push` | Uploaded the image to Docker Hub |

> 📌 Now **anyone in the world** can pull your image with: `docker pull your-username/flask-app:v1`

</details>

[↑ Back to top](#-docker-basics--from-zero-to-production)

---

## 11. Interview Prep — Core Ecosystem Questions

---

### 🟢 Beginner Level

<details>
<summary><b>Q11: What is a Docker Image?</b></summary>

A Docker Image is an **immutable snapshot** that contains everything an app needs to run — the code, libraries, dependencies, and a piece of the OS. It's read-only and portable. You create images using a Dockerfile.

</details>

<details>
<summary><b>Q12: What is a Docker Registry and why do we need it?</b></summary>

A Docker Registry is a **central storage place** for Docker images — like GitHub but for images. We need it so that teams can **share images** across machines. Example: Docker Hub is the most popular public registry.

</details>

<details>
<summary><b>Q13: What is a Dockerfile used for?</b></summary>

A Dockerfile is a **text file with instructions** that Docker reads to automatically build an image. Each line is a step — like `FROM` (pick a base image), `COPY` (copy files), `RUN` (run a command), and `CMD` (run the app).

</details>

---

### 🟡 Intermediate Level

<details>
<summary><b>Q14: Explain how Docker images, containers, Dockerfiles, registries, and orchestration fit together in a CI/CD pipeline.</b></summary>

The flow is:

1. **Dockerfile** — Developer writes instructions to build the app
2. **Image** — CI/CD pipeline runs `docker build` and creates an image
3. **Registry** — The image is pushed to a registry (e.g., AWS ECR) for storage
4. **Container** — The production server pulls the image and runs it as a container
5. **Orchestration** — Kubernetes (or similar) manages the containers — scaling, healing, and load balancing

> **One-liner:** Dockerfile → Image → Registry → Container → Orchestration

</details>

<details>
<summary><b>Q15: Why do enterprises use private registries instead of Docker Hub?</b></summary>

Public registries like Docker Hub can contain **unverified or vulnerable images**. Private registries (like AWS ECR, Harbor, or Azure ACR) give companies **full control** over who can access their images, making them more secure for production environments.

</details>

---

### 🔴 Advanced Level

<details>
<summary><b>Q16: If your containerized app runs locally but fails in Kubernetes, how would you debug it?</b></summary>

Step-by-step:

1. **Check pod logs** → `kubectl logs pod-name`
2. **Describe the pod** → `kubectl describe pod pod-name` (shows events, errors, resource issues)
3. **Verify the image** → Make sure the correct image version was pulled from the registry
4. **Check environment variables** → Kubernetes config might be different from local
5. **Inspect networking** → Is the app trying to reach another service? Check if it's reachable inside the cluster
6. **Check resource limits** → Kubernetes sets CPU/memory limits — your container might be getting killed for using too much

</details>

<details>
<summary><b>Q17: Why do we need container orchestration? When is it overkill?</b></summary>

**Why we need it:** When you have many containers, you need automatic scaling, load balancing, self-healing, and rolling updates. Orchestration handles all of this.

**When it's overkill:**
- You only have 1–2 containers
- You're building a small project or prototype
- You don't need auto-scaling or high availability

> **Rule of thumb:** If you have a single container or a small app, use `docker run`. If you have multiple services that need to scale and stay healthy, use Kubernetes.

</details>

<details>
<summary><b>Q18: What is the difference between EXPOSE and -p in Docker?</b></summary>

| | What It Does |
|---|---|
| **`EXPOSE 5000`** (in Dockerfile) | Documents which port the app uses inside the container. It does **not** actually open the port. |
| **`-p 5000:5000`** (in `docker run`) | Actually **maps** a port on your machine to a port inside the container. This is what makes the app accessible. |

> **Short answer:** `EXPOSE` is just documentation. `-p` is what actually opens the port.

</details>

[↑ Back to top](#-docker-basics--from-zero-to-production)

---

## 🗂️ This Repo — File Map

This is **docker-basics.md** — your foundation. Everything else builds on top of it.

| File | What It Covers | Status |
|------|----------------|--------|
| **docker-basics.md** | What Docker is, core concepts, 5 pillars, 18 interview Q&A | ✅ You are here |
| `docker-compose.md` | Run multiple containers together (app + database) | 🔜 Coming next |
| `docker-networking.md` | How containers talk to each other | 🔜 Coming next |
| `docker-volumes.md` | Data persistence — don't lose your data | 🔜 Coming next |
| `docker-hub.md` | Push, pull, and manage images on Docker Hub | 🔜 Coming next |
| `docker-cicd.md` | Automate testing and deployment with Docker | 🔜 Coming next |
| `kubernetes-basics.md` | The next big step — container orchestration at scale | 🔜 Coming next |

---
## ⭐ If this helped you, star the repo.
