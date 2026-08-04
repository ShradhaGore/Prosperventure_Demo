# Prosperventure Demo - DevOps Internship Project

## 📖 Project Overview

This project was completed as part of my DevOps internship. The main objective of this project was to understand how a MERN Stack application can be deployed using modern DevOps tools and practices.

Instead of developing the application from scratch, the focus of this project was on the deployment process. The project covers source code management using Git and GitHub, containerization using Docker, image management using Docker Hub, deployment using Kubernetes (Minikube), and automation using Jenkins CI/CD Pipeline.

The complete implementation was performed in a Linux environment using WSL Ubuntu on Windows.

Throughout this project, I gained hands-on experience with Git, GitHub, Linux, Docker, Kubernetes, Jenkins, and CI/CD concepts.

---

# 🎯 Objectives

- Understand the complete DevOps workflow.
- Learn Git and GitHub for version control.
- Containerize the MERN Stack application using Docker.
- Build and manage Docker images.
- Deploy the application using Kubernetes.
- Automate deployment using Jenkins Pipeline.
- Gain practical knowledge of CI/CD concepts.
- Understand how different DevOps tools work together.

---

# 🛠️ Tech Stack

## Application Stack

### Frontend
- React.js
- Vite

### Backend
- Node.js
- Express.js

### Database
- MongoDB Atlas

## DevOps Tools

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

```text
Prosperventure_Demo/

│
├── client/
│   ├── Dockerfile
│   └── React Frontend Application
│
├── server/
│   ├── Dockerfile
│   └── Express Backend Application
│
├── k8s/
│   ├── backend-deployment.yaml
│   ├── backend-service.yaml
│   ├── frontend-deployment.yaml
│   └── frontend-service.yaml
│
├── Jenkinsfile
├── architecture.png
├── screenshots/
├── README.md
└── .gitignore

⚙️ Project Workflow
Git & GitHub
Cloned the existing Prosperventure project.
Created a personal GitHub repository.
Managed project versions using Git.
Stored application code and DevOps configuration files.
🐳 Docker Containerization

Docker was used to containerize the frontend and backend applications.

Backend Container

Steps performed:

Created Dockerfile for Node.js and Express.js application.
Installed required dependencies.
Built backend Docker image.
Tested backend using Docker container.
Frontend Container

Steps performed:

Created Dockerfile for React.js application.
Installed required dependencies.
Built frontend Docker image.
Tested frontend using Docker container.

Docker helped package the application with all required dependencies.

📦 Docker Hub

After creating Docker images locally:

Docker images were tagged.
Images were pushed to Docker Hub.
Docker Hub was used as a container image repository.
☸️ Kubernetes Deployment

The application was deployed locally using Kubernetes with Minikube.

Created Kubernetes resources:

Backend Deployment
Backend Service
Frontend Deployment
Frontend Service

Commands used:

kubectl apply -f k8s/

Check Pods:

kubectl get pods

Check Services:

kubectl get services
🔄 Jenkins CI/CD Pipeline

Jenkins was used to automate the deployment process.

Pipeline steps:

Pull source code from GitHub.
Build frontend and backend Docker images.
Load Docker images into Minikube.
Deploy application using Kubernetes YAML files.
Verify deployment status.

Workflow:

GitHub Repository
        |
        ↓
Jenkins Pipeline
        |
        ↓
Docker Image Build
        |
        ↓
Kubernetes Deployment
        |
        ↓
Running Application


🏗️ DevOps Architecture Diagram

Developer
    |
    ↓
GitHub Repository
    |
    ↓
Jenkins CI/CD Pipeline
    |
    ↓
Docker Image Build
    |
    ↓
Docker Hub Registry
    |
    ↓
Kubernetes (Minikube)
    |
    ↓
Running Application



⚠️ Challenges Faced

During this project, I faced practical challenges:

Docker permission issues.
Docker image build errors.
Dependency installation issues.
Kubernetes deployment configuration.
Jenkins pipeline configuration.
Minikube setup issues.
Frontend and backend connectivity issues.

Resolving these challenges helped me understand the practical working of DevOps tools.

🎓 Learning Outcomes

Through this project, I learned:

Git and GitHub workflow.
Linux command-line basics using WSL Ubuntu.
Docker image creation and containerization.
Docker Hub image management.
Kubernetes Deployments and Services.
Jenkins CI/CD Pipeline creation.
Application deployment troubleshooting.

This project gave me hands-on experience in deploying and managing a MERN Stack application using DevOps tools.

📸 Project Screenshots
GitHub Repository

Docker Images

Docker Containers

Kubernetes Pods

Kubernetes Services

Jenkins Pipeline Success

Application Running

✅ Conclusion

This project helped me understand the complete DevOps lifecycle from source code management to automated deployment.

By implementing Git, Docker, Jenkins, and Kubernetes together, I gained practical knowledge of CI/CD workflows and how DevOps tools work together for application deployment.

The complete deployment pipeline was successfully implemented and tested using a local Kubernetes environment with Minikube.
