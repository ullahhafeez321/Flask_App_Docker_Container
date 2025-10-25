# 🐳 Flask App in Docker

<<<<<<< HEAD
A production-ready Flask application containerized with Docker and ready for Kubernetes deployment.

![Docker](https://img.shields.io/badge/Docker-✓-blue?logo=docker)
![Flask](https://img.shields.io/badge/Flask-✓-green?logo=flask)
![Kubernetes](https://img.shields.io/badge/Kubernetes-✓-blue?logo=kubernetes)
=======
![Docker](https://img.shields.io/badge/Docker-✓-blue?logo=docker)
![Flask](https://img.shields.io/badge/Flask-✓-green?logo=flask)
![Kubernetes](https://img.shields.io/badge/Kubernetes-✓-blue?logo=kubernetes)

This repository contains a simple **Python Flask web application** that displays:

> **"Hello from my Docker Container."**
>>>>>>> 3bc23d7af4d4bb3a3215558409f76436f8330140

## 📋 Overview

This project demonstrates a modern approach to containerizing a Python Flask application with Docker and deploying it to Kubernetes. It serves as a complete example for learning containerization and orchestration technologies.

<<<<<<< HEAD
## ✨ Features
=======
## 🚀 Features
- Simple Flask web app (`app.py`)
- Dockerfile for containerization  
- Step-by-step setup instructions
- Optional Kubernetes deployment guide
>>>>>>> 3bc23d7af4d4bb3a3215558409f76436f8330140

- **🚀 Production Ready Flask App** - Optimized for container environments
- **🐳 Multi-stage Docker Build** - Small, secure final image
- **⚙️ Environment Configuration** - Separate settings for dev/prod
- **🔍 Health Checks** - Container health monitoring endpoints
- **☸️ Kubernetes Ready** - Complete deployment manifests
- **📊 Logging** - Structured application logging

## 📁 Project Structure

```
<<<<<<< HEAD
flask-docker-app/
├── app.py                 # Main Flask application
├── requirements.txt       # Python dependencies
├── Dockerfile            # Multi-stage Docker build
├── .dockerignore         # Files to exclude from Docker build
├── docker-compose.yml    # Development environment
├── deployment.yaml       # Kubernetes deployment
├── service.yaml          # Kubernetes service
└── README.md            # Project documentation
```

## 🛠️ Prerequisites

- **Docker** (20.10+) - [Install Docker](https://docs.docker.com/get-docker/)
- **Docker Compose** (optional) - Included with Docker Desktop
- **Kubernetes CLI** (optional) - For Kubernetes deployment
=======
📁 flask_app_project/
│
├── 🐍 app.py              # Flask web app file
├── 🐳 Dockerfile          # Instructions to build the Docker image
├── 📋 requirements.txt    # Python dependencies
└── 📖 README.md          # Documentation and usage guide
```
>>>>>>> 3bc23d7af4d4bb3a3215558409f76436f8330140

## 🚀 Quick Start

### Method 1: Using Docker Run

```bash
<<<<<<< HEAD
# Clone the repository
git clone https://github.com/your-username/flask-docker-app.git
cd flask-docker-app

# Build the Docker image
docker build -t flask-app .

# Run the container
docker run -d -p 5000:5000 --name flask-container flask-app

# Verify it's working
curl http://localhost:5000
```

### Method 2: Using Docker Compose (Recommended)

```bash
# Start the application
docker-compose up -d

# View logs
docker-compose logs -f

# Check health
curl http://localhost:5000/health

# Stop the application
docker-compose down
```

## 🌐 Access the Application

Once running, access the application at:
- **Main Page**: http://localhost:5000
- **Health Check**: http://localhost:5000/health

You should see:
```
Hello from my Docker Container!
```

## 🐳 Docker Commands Reference
=======
git clone https://github.com/ullahhafeez321/Flask_App_Docker_Container.git
cd Flask_App_Docker_Container
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
>>>>>>> 3bc23d7af4d4bb3a3215558409f76436f8330140

### Building and Running
```bash
# Build image
docker build -t flask-app .

<<<<<<< HEAD
# Run container
docker run -d -p 5000:5000 --name flask-container flask-app

# Run with environment variables
docker run -d -p 5000:5000 -e FLASK_ENV=production --name flask-container flask-app
```

### Management
```bash
# View running containers
docker ps

# View container logs
docker logs flask-container

# Stop container
docker stop flask-container

# Remove container
docker rm flask-container

# Remove image
docker rmi flask-app
```

### Debugging
```bash
# Run in interactive mode
docker run -it -p 5000:5000 flask-app

# Execute commands in running container
docker exec -it flask-container /bin/sh

# Inspect container details
docker inspect flask-container
```

## ☸️ Kubernetes Deployment

### Prerequisites
- Kubernetes cluster (Minikube, kind, or cloud provider)
- kubectl configured
- Docker image pushed to a registry

### Step 1: Push Image to Registry
```bash
# Tag the image
docker tag flask-app your-username/flask-app:latest

# Push to Docker Hub
docker push your-username/flask-app:latest
```

### Step 2: Deploy to Kubernetes

```bash
# Create deployment
kubectl apply -f deployment.yaml

# Create service
kubectl apply -f service.yaml

# Check deployment status
kubectl get deployments
kubectl get pods
kubectl get services

# Access the application
minikube service flask-service --url
```

### Kubernetes Management
```bash
# Scale deployment
kubectl scale deployment flask-deployment --replicas=3

# View logs
kubectl logs -l app=flask-app

# Delete resources
kubectl delete -f deployment.yaml -f service.yaml
```

## 📊 Kubernetes Manifests

### deployment.yaml
=======
### Step 1 — Push the Docker image to Docker Hub:
```bash
docker tag flask_app yourusername/flask_app:latest
docker push yourusername/flask_app:latest
```

### Step 2 — Create a deployment file `deployment.yaml`:
>>>>>>> 3bc23d7af4d4bb3a3215558409f76436f8330140
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: flask-deployment
  labels:
    app: flask-app
spec:
  replicas: 3
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
        image: your-username/flask-app:latest
        ports:
        - containerPort: 5000
<<<<<<< HEAD
        env:
        - name: FLASK_ENV
          value: "production"
        livenessProbe:
          httpGet:
            path: /health
            port: 5000
          initialDelaySeconds: 5
          periodSeconds: 10
        readinessProbe:
          httpGet:
            path: /health
            port: 5000
          initialDelaySeconds: 2
          periodSeconds: 5
```

### service.yaml
```yaml
apiVersion: v1
kind: Service
metadata:
  name: flask-service
spec:
  selector:
    app: flask-app
  ports:
  - port: 80
    targetPort: 5000
  type: LoadBalancer
```

## 🔧 Development

### Local Development (Without Docker)
```bash
# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run locally
python app.py
```

### Testing
```bash
# Test the application
curl http://localhost:5000
curl http://localhost:5000/health

# Test with different environments
FLASK_ENV=production python app.py
```

## 🐛 Troubleshooting

### Common Issues
=======
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
>>>>>>> 3bc23d7af4d4bb3a3215558409f76436f8330140

**Port already in use:**
```bash
# Find process using port 5000
lsof -i :5000

<<<<<<< HEAD
# Kill the process or use different port
docker run -d -p 5001:5000 --name flask-container flask-app
```

**Container fails to start:**
```bash
# Check logs
docker logs flask-container

# Run with interactive mode to see errors
docker run -it -p 5000:5000 flask-app
```

**Image build failures:**
```bash
# Clean build
docker build --no-cache -t flask-app .

# Check disk space
docker system df
```

## 📈 Monitoring

### Application Health
```bash
# Health check endpoint
curl http://localhost:5000/health

# Container health (Docker 1.12+)
docker ps --filter "name=flask-container"
```

### Performance
```bash
# Container stats
docker stats flask-container

# Resource usage
docker system df
```

## 🔒 Security Best Practices

- Use non-root user in container
- Regular security updates
- Scan images for vulnerabilities
- Use secrets for sensitive data
- Limit container capabilities

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 👨‍💻 Author

**Hafeez Ullah**  
- Course: Containerization and Orchestration  
- Project: Docker & Kubernetes Flask Example

## 🙏 Acknowledgments

- Flask community for the excellent web framework
- Docker documentation and examples
- Kubernetes community for orchestration tools

---

**Happy Containerizing! 🐳**
=======
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
>>>>>>> 3bc23d7af4d4bb3a3215558409f76436f8330140
