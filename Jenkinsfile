pipeline {
    agent any
    environment {
       DOCKER_HUB_CREDENTIALS = credentials('dockerhub-credentials')'
    }
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/riya-mozumdar/project-orbit.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("riya2125/example")
                }
            }
        }
        stage('Push Docker Image to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('docker.withRegistry(
    'https://index.docker.io/v1/',
    'dockerhub-credentials'
) {
                        def app = docker.build("riya2125/example")
                        app.push('latest')
                    }
                }
            }
        }
    }
}
