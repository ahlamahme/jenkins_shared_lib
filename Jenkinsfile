pipeline {
    agent any
    
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image from the Dockerfile
                    docker.build('ahlamahmed/flask:latest', '-f Dockerfile .')
                    
                    // Optionally, push the built Docker image to a registry
                    docker.withRegistry('https://index.docker.io/v1/', 'DuckerHub') {
                        docker.image('ahlamahmed/flask:latest').push()
                    }
                }
            }
        }
    }
}
