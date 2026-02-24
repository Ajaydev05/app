pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = 'dockerhub-credentials-id'
        DOCKERHUB_USERNAME = 'your-dockerhub-username'

        FRONTEND_IMAGE = "${DOCKERHUB_USERNAME}/mean-frontend"
        BACKEND_IMAGE  = "${DOCKERHUB_USERNAME}/mean-backend"

        IMAGE_TAG = "latest"
    }

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/your-username/mean-app.git'
            }
        }

        stage('Build Frontend Image') {
            steps {
                script {
                    docker.build("${FRONTEND_IMAGE}:${IMAGE_TAG}", "./frontend")
                }
            }
        }

        stage('Build Backend Image') {
            steps {
                script {
                    docker.build("${BACKEND_IMAGE}:${IMAGE_TAG}", "./backend")
                }
            }
        }

        stage('Login to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('', DOCKERHUB_CREDENTIALS) {
                        echo "Logged in to Docker Hub"
                    }
                }
            }
        }

        stage('Push Frontend Image') {
            steps {
                script {
                    docker.withRegistry('', DOCKERHUB_CREDENTIALS) {
                        docker.image("${FRONTEND_IMAGE}:${IMAGE_TAG}").push()
                    }
                }
            }
        }

        stage('Push Backend Image') {
            steps {
                script {
                    docker.withRegistry('', DOCKERHUB_CREDENTIALS) {
                        docker.image("${BACKEND_IMAGE}:${IMAGE_TAG}").push()
                    }
                }
            }
        }

        stage('Deploy using Docker Compose') {
            steps {
                sh 'docker-compose down'
                sh 'docker-compose up -d'
            }
        }
    }

    post {
        success {
            echo 'Images successfully pushed to Docker Hub'
        }

        failure {
            echo 'Pipeline failed'
        }
    }
}