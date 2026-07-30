pipeline {
    agent any

    environment {
        DOCKER_BUILDKIT = '0'
        HOME = '/var/lib/jenkins'
        MINIKUBE_HOME = '/var/lib/jenkins/.minikube'
        KUBECONFIG = '/var/lib/jenkins/.kube/config'
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
                sh 'kubectl get services'
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
