pipeline {
    agent any

    environment {
        DOCKER_BUILDKIT = '0'
    }

    stages {

        stage('Build Backend Docker Image') {
            steps {
                dir('server') {
                    sh '''
                    export DOCKER_BUILDKIT=0
                    docker build -t backend-image .
                    '''
                }
            }
        }

        stage('Build Frontend Docker Image') {
            steps {
                dir('client') {
                    sh '''
                    export DOCKER_BUILDKIT=0
                    docker build -t frontend-image .
                    '''
                }
            }
        }

        stage('Load Images into Minikube') {
            steps {
                withEnv([
                    'HOME=/home/gore',
                    'MINIKUBE_HOME=/home/gore/.minikube',
                    'KUBECONFIG=/home/gore/.kube/config'
                ]) {
                    sh 'minikube image load backend-image'
                    sh 'minikube image load frontend-image'
                }
            }
        }

        stage('Deploy Backend') {
            steps {
                withEnv([
                    'HOME=/home/gore',
                    'MINIKUBE_HOME=/home/gore/.minikube',
                    'KUBECONFIG=/home/gore/.kube/config'
                ]) {
                    dir('k8s') {
                        sh 'kubectl apply -f backend-deployment.yaml'
                        sh 'kubectl apply -f backend-service.yaml'
                    }
                }
            }
        }

        stage('Deploy Frontend') {
            steps {
                withEnv([
                    'HOME=/home/gore',
                    'MINIKUBE_HOME=/home/gore/.minikube',
                    'KUBECONFIG=/home/gore/.kube/config'
                ]) {
                    dir('k8s') {
                        sh 'kubectl apply -f frontend-deployment.yaml'
                        sh 'kubectl apply -f frontend-service.yaml'
                    }
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                withEnv([
                    'HOME=/home/gore',
                    'MINIKUBE_HOME=/home/gore/.minikube',
                    'KUBECONFIG=/home/gore/.kube/config'
                ]) {
                    sh 'kubectl get deployments'
                    sh 'kubectl get pods'
                    sh 'kubectl get services'
                }
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
