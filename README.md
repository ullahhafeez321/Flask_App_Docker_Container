# 🐳 Flask App in Docker

A production-ready Flask application containerized with Docker and ready for Kubernetes deployment.

![Docker](https://img.shields.io/badge/Docker-✓-blue?logo=docker)
![Flask](https://img.shields.io/badge/Flask-✓-green?logo=flask)
![Kubernetes](https://img.shields.io/badge/Kubernetes-✓-blue?logo=kubernetes)

## 📋 Overview

This project demonstrates a modern approach to containerizing a Python Flask application with Docker and deploying it to Kubernetes. It serves as a complete example for learning containerization and orchestration technologies.

## ✨ Features

- **🚀 Production Ready Flask App** - Optimized for container environments
- **🐳 Multi-stage Docker Build** - Small, secure final image
- **⚙️ Environment Configuration** - Separate settings for dev/prod
- **🔍 Health Checks** - Container health monitoring endpoints
- **☸️ Kubernetes Ready** - Complete deployment manifests
- **📊 Logging** - Structured application logging

## 📁 Project Structure

```
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

## 🚀 Quick Start

### Method 1: Using Docker Run

```bash
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

### Building and Running
```bash
# Build image
docker build -t flask-app .

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

**Port already in use:**
```bash
# Find process using port 5000
lsof -i :5000

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