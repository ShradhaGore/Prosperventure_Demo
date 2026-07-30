# 🚀 Prosperventure Demo – DevOps CI/CD Pipeline

## 📖 Project Overview

This project demonstrates an end-to-end DevOps implementation for a MERN Stack application. The original application source code was used as the base project, and the deployment pipeline was designed and implemented using modern DevOps tools.

The project includes containerization with Docker, orchestration using Kubernetes (Minikube), and automation through Jenkins CI/CD.

---

## 🛠️ Technologies Used

- Git & GitHub
- Linux (WSL Ubuntu)
- Docker
- Docker Hub
- Kubernetes
- Minikube
- Jenkins
- Node.js
- React.js
- Express.js
- MongoDB Atlas

---

## 📂 Project Structure

```
Prosperventure_Demo/
│
├── client/
│   ├── Dockerfile
│   └── React Frontend
│
├── server/
│   ├── Dockerfile
│   └── Express Backend
│
├── k8s/
│   ├── backend-deployment.yaml
│   ├── backend-service.yaml
│   ├── frontend-deployment.yaml
│   └── frontend-service.yaml
│
├── Jenkinsfile
└── README.md
```

---

# 🚀 DevOps Workflow

### 1. Clone Repository

```bash
git clone <repository-url>
```

### 2. Build Docker Images

```bash
docker build -t backend-image ./server
docker build -t frontend-image ./client
```

### 3. Deploy on Kubernetes

```bash
kubectl apply -f k8s/
```

### 4. Verify Deployment

```bash
kubectl get pods
kubectl get svc
kubectl get deployments
```

### 5. Access Application

```bash
minikube service frontend-service
```

---

# 🔄 Jenkins CI/CD Pipeline

The Jenkins pipeline performs the following steps automatically:

- Clone the GitHub repository
- Build Backend Docker Image
- Build Frontend Docker Image
- Load Docker Images into Minikube
- Deploy Backend on Kubernetes
- Deploy Frontend on Kubernetes
- Verify Kubernetes Deployment

---

# ☸️ Kubernetes Resources

- Backend Deployment
- Backend Service
- Frontend Deployment
- Frontend Service

---

# 🐳 Docker

Separate Dockerfiles were created for:

- Backend
- Frontend

Docker images are built automatically through Jenkins.

---

# 💡 Skills Demonstrated

- CI/CD Pipeline
- Docker
- Kubernetes
- Jenkins
- Git & GitHub
- Linux
- Containerization
- YAML
- MERN Stack Deployment

---

# 👩‍💻 Author

**Shradha Gore**

DevOps Engineer | MERN Deployment | Docker | Kubernetes | Jenkins
