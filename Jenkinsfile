pipeline {
    agent any

    environment {
        DOCKER_BUILDKIT = '0'
        HOME = '/var/lib/jenkins'
        MINIKUBE_HOME = '/var/lib/jenkins/.minikube'
        KUBECONFIG = '/var/lib/jenkins/.kube/config'
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Backend Docker Image') {
            steps {
                dir('server') {
                    sh '''
                        docker build -t backend-image:latest .
                    '''
                }
            }
        }

        stage('Build Frontend Docker Image') {
            steps {
                dir('client') {
                    sh '''
                        docker build -t frontend-image:latest .
                    '''
                }
            }
        }

        stage('Refresh Kubernetes Config') {
            steps {
                sh '''
                    sudo mkdir -p /var/lib/jenkins/.kube
                    sudo cp /home/gore/.kube/config /var/lib/jenkins/.kube/config
                    sudo chown -R jenkins:jenkins /var/lib/jenkins/.kube
                '''
            }
        }

        stage('Verify Minikube') {
            steps {
                sh '''
                    minikube status
                    kubectl cluster-info
                    kubectl get nodes
                '''
            }
        }

        stage('Load Images into Minikube') {
            steps {
                sh '''
                    minikube image load backend-image:latest
                    minikube image load frontend-image:latest
                '''
            }
        }

        stage('Deploy Backend') {
            steps {
                dir('k8s') {
                    sh '''
                        kubectl apply -f backend-deployment.yaml
                        kubectl apply -f backend-service.yaml
                    '''
                }
            }
        }

        stage('Deploy Frontend') {
            steps {
                dir('k8s') {
                    sh '''
                        kubectl apply -f frontend-deployment.yaml
                        kubectl apply -f frontend-service.yaml
                    '''
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                sh '''
                    kubectl get deployments
                    kubectl get pods
                    kubectl get services
                '''
            }
        }
    }

    post {
        always {
            echo 'Pipeline Finished!'
        }

        success {
            echo 'Deployment Successful!'
        }

        failure {
            echo 'Deployment Failed!'
        }
    }
}
