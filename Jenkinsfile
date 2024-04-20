pipeline {
    agent any
    
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    // Clone the GitHub repository containing the Dockerfile
                    checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/ahlamahme/jenkins_shared_lib.git']]])
                    
                    // Build the Docker image
                    docker.build('yourusername/yourimage:latest', '-f Dockerfile .')
                }
            }
        }
    }
}
