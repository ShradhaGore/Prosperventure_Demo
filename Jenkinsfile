pipeline {
    agent any

    environment {
        DOCKER_BUILDKIT = '0'
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

        stage('Verify Minikube') {
            steps {
                sh '''
                sudo -u gore bash -c '
                export HOME=/home/gore
                export MINIKUBE_HOME=/home/gore/.minikube
                export KUBECONFIG=/home/gore/.kube/config

                minikube status
                kubectl cluster-info
                kubectl get nodes
                '
                '''
            }
        }

        stage('Load Images into Minikube') {
            steps {
                sh '''
                sudo -u gore bash -c '
                export HOME=/home/gore
                export MINIKUBE_HOME=/home/gore/.minikube
                export KUBECONFIG=/home/gore/.kube/config

                minikube image load backend-image:latest
                minikube image load frontend-image:latest
                '
                '''
            }
        }

        stage('Deploy Backend') {
            steps {
                dir('k8s') {
                    sh '''
                    sudo -u gore bash -c '
                    export HOME=/home/gore
                    export MINIKUBE_HOME=/home/gore/.minikube
                    export KUBECONFIG=/home/gore/.kube/config

                    kubectl apply -f backend-deployment.yaml
                    kubectl apply -f backend-service.yaml
                    '
                    '''
                }
            }
        }

        stage('Deploy Frontend') {
            steps {
                dir('k8s') {
                    sh '''
                    sudo -u gore bash -c '
                    export HOME=/home/gore
                    export MINIKUBE_HOME=/home/gore/.minikube
                    export KUBECONFIG=/home/gore/.kube/config

                    kubectl apply -f frontend-deployment.yaml
                    kubectl apply -f frontend-service.yaml
                    '
                    '''
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                sh '''
                sudo -u gore bash -c '
                export HOME=/home/gore
                export MINIKUBE_HOME=/home/gore/.minikube
                export KUBECONFIG=/home/gore/.kube/config

                kubectl get deployments
                kubectl get pods
                kubectl get services
                '
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
