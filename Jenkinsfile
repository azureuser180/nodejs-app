pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build and Push Docker Image') {
            steps {
                script {
                    def dockerImage = docker.build("ashraf313/hello-world-nodejs:${env.BUILD_NUMBER}")
                    dockerImage.withRegistry('https://registry.hub.docker.com', 'DOCKER_USERNAME', 'DOCKER_PASSWORD') {
                        dockerImage.push()
                    }
                }
            }
        }
    }
}

