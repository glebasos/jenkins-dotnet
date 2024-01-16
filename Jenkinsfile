pipeline {
    agent {
        label 'jenkins-agentsocat' // Replace with your specific agent label
    }

    environment {
        DOCKER_IMAGE = 'realjenkshit:latest'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build Docker image using Dockerfile
                    docker.build("${DOCKER_IMAGE}", ".")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Run Docker container from the built image
                    docker.image("${DOCKER_IMAGE}").run('-p 8098:8098')
                }
            }
        }
    }
}