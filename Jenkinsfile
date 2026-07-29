pipeline {
    agent any

    environment {
        HOME = "/home/gore"
        MINIKUBE_HOME = "/home/gore/.minikube"
        KUBECONFIG = "/home/gore/.kube/config"
    }

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
            steps {
                sh 'minikube image load backend-image'
                sh 'minikube image load frontend-image'
            }
        }

        stage('Deploy Backend') {
            steps {
                dir('k8s') {
                    sh 'kubectl apply -f backend-deployment.yaml'
                    sh 'kubectl apply -f backend-service.yaml'
                }
            }
        }

        stage('Deploy Frontend') {
            steps {
                dir('k8s') {
                    sh 'kubectl apply -f frontend-deployment.yaml'
                    sh 'kubectl apply -f frontend-service.yaml'
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                sh 'kubectl get deployments'
                sh 'kubectl get pods'
                sh 'kubectl get svc'
            }
        }

    }
}
     
