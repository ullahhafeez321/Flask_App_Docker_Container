# 🐳 Flask App in Docker

![Docker](https://img.shields.io/badge/Docker-✓-blue?logo=docker)
![Flask](https://img.shields.io/badge/Flask-✓-green?logo=flask)
![Kubernetes](https://img.shields.io/badge/Kubernetes-✓-blue?logo=kubernetes)

This repository contains a simple **Python Flask web application** that displays:

> **"Hello from my Docker Container."**

It demonstrates the basics of **Docker containerization** — including how to build an image, run a container, and access the app in your browser.  
Additionally, it provides steps for optional deployment to **Kubernetes**.

---

## 🚀 Features
- Simple Flask web app (`app.py`)
- Dockerfile for containerization  
- Step-by-step setup instructions
- Optional Kubernetes deployment guide

---

## 🗂️ Project Structure

```
📁 flask_app_project/
│
├── 🐍 app.py              # Flask web app file
├── 🐳 Dockerfile          # Instructions to build the Docker image
├── 📋 requirements.txt    # Python dependencies
└── 📖 README.md          # Documentation and usage guide
```

---

## 🧰 Requirements
- [Docker](https://www.docker.com/products/docker-desktop) installed  
- (Optional) Python 3.9+ if testing without Docker

---

## ⚙️ How to Run Locally with Docker

### Step 1 — Clone the Repository
```bash
git clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>
```

### Step 2 — Build the Docker Image
```bash
docker build -t flask_app .
```

**Expected Output:**
```
[+] Building 45.3s (8/8) FINISHED
 => [internal] load build definition from Dockerfile
 => => transferring dockerfile: 37B
 => [internal] load .dockerignore
 => => transferring context: 2B
 => [internal] load metadata for docker.io/library/python:3.9-slim
 => [1/3] FROM docker.io/library/python:3.9-slim
 => [2/3] COPY requirements.txt .
 => [3/3] RUN pip install -r requirements.txt
 => exporting to image
 => => writing image sha256:7d...
 => => naming to docker.io/library/flask_app
```

### Step 3 — Run the Container
```bash
docker run -d -p 5000:5000 --name flask_container flask_app
```

**Expected Output:**
```
d1b4c3a8e5f6a7b8c9d0e1f2a3b4c5d6e7f8a9b0c1d2e3f4a5b6c7d8e9f0a1b2
```

### Step 4 — Open in Browser

Visit 👉 **http://localhost:5000**

**You'll see:**
```
Hello from my Docker Container.
```

---

## 🧹 Optional Commands

### Stop container:
```bash
docker stop flask_container
```

### Remove container:
```bash
docker rm flask_container
```

### View running containers:
```bash
docker ps
```

### View container logs:
```bash
docker logs flask_container
```

---

## ☸️ Deploying on Kubernetes (Optional)

To deploy this app using Kubernetes:

### Step 1 — Push the Docker image to Docker Hub:
```bash
docker tag flask_app yourusername/flask_app:latest
docker push yourusername/flask_app:latest
```

### Step 2 — Create a deployment file `deployment.yaml`:
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: flask-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: flask-app
  template:
    metadata:
      labels:
        app: flask-app
    spec:
      containers:
      - name: flask-container
        image: yourusername/flask_app:latest
        ports:
        - containerPort: 5000
```

### Step 3 — Apply it to the cluster:
```bash
kubectl apply -f deployment.yaml
```

### Step 4 — Expose it:
```bash
kubectl expose deployment flask-deployment --type=NodePort --port=5000
```

### Step 5 — Check your deployment:
```bash
kubectl get deployments
kubectl get pods
kubectl get services
```

---

## 🐳 Docker Commands Cheat Sheet

| Command | Description |
|---------|-------------|
| `docker build -t flask_app .` | Build Docker image |
| `docker images` | List all images |
| `docker run -d -p 5000:5000 flask_app` | Run container in background |
| `docker ps` | Show running containers |
| `docker stop <container_id>` | Stop a container |
| `docker rm <container_id>` | Remove a container |
| `docker rmi flask_app` | Remove an image |

---

## 👨‍💻 Author

**Name:** Hafeez Ullah  
**Course:** Containerization and Orchestration  
**Project:** Docker & Kubernetes Flask Example

---

## 🏷️ License

This project is open-source and free to use for educational purposes.

---

## ❓ Troubleshooting

### Port already in use?
```bash
# Use a different port
docker run -d -p 5001:5000 --name flask_container flask_app
```

### Container not starting?
```bash
# Check logs
docker logs flask_container

# Run in foreground to see errors
docker run -p 5000:5000 flask_app
```

### Build failing?
```bash
# Clean build
docker build --no-cache -t flask_app .
```

---

**Happy Coding! 🐳**
