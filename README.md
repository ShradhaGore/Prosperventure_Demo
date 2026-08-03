# 🚀 Prosperventure Demo - DevOps Internship Project

## 📖 Project Overview

This project was completed as part of my DevOps internship. The main objective of this project was to understand how a MERN Stack application can be deployed using modern DevOps tools and practices.

Instead of developing the application from scratch, the focus of this project was on the deployment process. The project covers containerization using Docker, image management with Docker Hub, deployment using Kubernetes (Minikube), and automation using Jenkins CI/CD Pipeline.

Throughout this project, I gained hands-on experience with Git, GitHub, Linux, Docker, Kubernetes, Jenkins, and CI/CD concepts.

---

# 🎯 Objectives

- Understand the complete DevOps workflow.
- Learn Git and GitHub for version control.
- Containerize the MERN Stack application using Docker.
- Push Docker images to Docker Hub.
- Deploy the application on Kubernetes using Minikube.
- Automate deployment using Jenkins Pipeline.
- Gain practical knowledge of CI/CD.

---

# 🛠️ Tech Stack

### Frontend
- React.js
- Vite

### Backend
- Node.js
- Express.js

### Database
- MongoDB Atlas

### DevOps Tools
- Git
- GitHub
- Linux (WSL Ubuntu)
- Docker
- Docker Hub
- Kubernetes
- Minikube
- Jenkins

---

# 📂 Project Structure

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
├── README.md
└── .gitignore
```

---

# ⚙️ Project Workflow

The project was completed in different phases.

### Git & GitHub

- Cloned the existing project.
- Created a personal GitHub repository.
- Managed project versions using Git.

### Docker

- Created Dockerfile for the backend.
- Created Dockerfile for the frontend.
- Built Docker images.
- Tested the application using Docker containers.

### Docker Hub

- Tagged Docker images.
- Pushed Docker images to Docker Hub.

### Kubernetes

- Installed Minikube.
- Created Kubernetes Deployment files.
- Created Kubernetes Service files.
- Deployed the application on Kubernetes.

### Jenkins

- Installed Jenkins.
- Created a Jenkins Pipeline.
- Connected Jenkins with GitHub.
- Automated the deployment process.

---
# 🐳 Docker

Docker was used to containerize both the frontend and backend applications.

### Backend
- Created a Dockerfile for the Express application.
- Installed all required dependencies.
- Exposed the backend port.
- Built the backend Docker image.

### Frontend
- Created a Dockerfile for the React application.
- Installed all required dependencies.
- Exposed the frontend port.
- Built the frontend Docker image.

Docker helped package the application with all its dependencies, making it easier to run in different environments.

---

# 📦 Docker Hub

After building the Docker images locally, they were tagged and pushed to Docker Hub. This allows the images to be stored in a central repository and used during deployment.

---

# ☸️ Kubernetes Deployment

The application was deployed locally using Kubernetes with Minikube.

The following Kubernetes resources were created:

- Backend Deployment
- Backend Service
- Frontend Deployment
- Frontend Service

Deployments were used to manage application Pods, while Services were used to expose the frontend and backend for communication.

---

# 🔄 Jenkins CI/CD Pipeline

Jenkins was used to automate the deployment process.

The pipeline performs the following tasks:

1. Clone the latest source code from GitHub.
2. Build Docker images for the backend and frontend.
3. Load Docker images into Minikube.
4. Deploy the application using Kubernetes manifests.
5. Verify the deployment.

This automation reduces manual work and helps deploy the latest version of the application more efficiently.

---

# 📊 CI/CD Workflow

The overall workflow followed in this project is shown below:

```

Developer
↓
GitHub Repository
↓
Jenkins Pipeline
↓
Docker Image Build
↓
Docker Hub
↓
Minikube (Kubernetes)
↓
Running Application

```

---

# ⚠️ Challenges Faced

During this project, I faced several practical challenges, including:

- Docker permission issues.
- Docker image build errors.
- Kubernetes deployment configuration.
- Jenkins pipeline configuration.
- Minikube setup.
- Frontend and backend connectivity issues.

Resolving these issues helped me better understand how DevOps tools work together in a real deployment environment.

---

# 🎓 Learning Outcomes

Through this project, I learned:

- Git and GitHub workflow.
- Linux command-line basics.
- Docker image creation and containerization.
- Docker Hub image management.
- Kubernetes Deployments and Services.
- Jenkins Pipeline creation.
- CI/CD concepts.
- Troubleshooting deployment-related issues.

This project gave me hands-on experience in deploying and managing a MERN Stack application using DevOps tools.

---

# 📸 Project Screenshots

The following screenshots can be added after completing the projects.
- GitHub Repository
- Docker Images
- Docker Containers
- Kubernetes Pods
- Kubernetes Services
- Jenkins Dashboard
- Successful Jenkins Pipeline
- Running Application

---
