pipeline {
    agent any

    stages {

        stage('Build Backend Docker Image') {
            steps {
                dir('server') {
                    sh 'docker build -t backend-image .'
                }
            }
        }

        stage('Build Frontend Docker Image') {
            steps {
                dir('client') {
                    sh 'docker build -t frontend-image .'
                }
            }
        }

        stage('Load Images into Minikube') {
            environment {
                MINIKUBE_HOME = '/home/gore/.minikube'
                KUBECONFIG = '/home/gore/.kube/config'
            }
            steps {
                sh 'HOME=/home/gore minikube image load backend-image'
                sh 'HOME=/home/gore minikube image load frontend-image'
            }
        }

        stage('Deploy Backend') {
            environment {
                MINIKUBE_HOME = '/home/gore/.minikube'
                KUBECONFIG = '/home/gore/.kube/config'
            }
            steps {
                dir('k8s') {
                    sh 'HOME=/home/gore kubectl apply -f backend-deployment.yaml'
                    sh 'HOME=/home/gore kubectl apply -f backend-service.yaml'
                }
            }
        }

        stage('Deploy Frontend') {
            environment {
                MINIKUBE_HOME = '/home/gore/.minikube'
                KUBECONFIG = '/home/gore/.kube/config'
            }
            steps {
                dir('k8s') {
                    sh 'HOME=/home/gore kubectl apply -f frontend-deployment.yaml'
                    sh 'HOME=/home/gore kubectl apply -f frontend-service.yaml'
                }
            }
        }

        stage('Verify Deployment') {
            environment {
                MINIKUBE_HOME = '/home/gore/.minikube'
                KUBECONFIG = '/home/gore/.kube/config'
            }
            steps {
                sh 'HOME=/home/gore kubectl get deployments'
                sh 'HOME=/home/gore kubectl get pods'
                sh 'HOME=/home/gore kubectl get svc'
            }
        }

    }
}    
