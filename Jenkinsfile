pipeline {
    agent any
    
    environment {
        DOCKER_HUB_CREDENTIALS = credentials('DuckerHub')
    }
    
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image from the Dockerfile
                    docker.build('ahlamahmed/flask:latest', '-f Dockerfile .')
                    
                    // Optionally, push the built Docker image to Docker Hub
                    docker.withRegistry('https://index.docker.io/v1/', DOCKER_HUB_CREDENTIALS) {
                        docker.image('ahlamahmed/flask:latest').push()
                    }
                }
            }
        }
    }
}
