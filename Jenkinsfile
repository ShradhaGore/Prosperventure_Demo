pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/RupeshMaster/Prosperventure_Demo.git'
            }
        }

        stage('Build Backend Image') {
            steps {
                sh 'cd server && docker build -t prosperventure-backend:v1 .'
            }
        }

        stage('Build Frontend Image') {
            steps {
                sh 'cd client && docker build -t prosperventure-frontend:v1 .'
            }
        }

        stage('Run Backend Container') {
            steps {
                sh '''
                docker rm -f prosperventure-backend-container || true
                docker run -d --name prosperventure-backend-container \
                -p 10000:10000 \
                --env-file server/.env \
                prosperventure-backend:v1
                '''
            }
        }

        stage('Run Frontend Container') {
            steps {
                sh '''
                docker rm -f prosperventure-frontend-container || true
                docker run -d --name prosperventure-frontend-container \
                -p 5173:5173 \
                prosperventure-frontend:v1
                '''
            }
        }
    }
}
