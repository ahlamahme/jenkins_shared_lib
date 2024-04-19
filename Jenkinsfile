pipeline {
    agent any
    
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    // Import Docker pipeline steps
                    def docker = container('docker')
                    
                    // Clone the GitHub repository containing the Dockerfile
                    checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/ahlamahme/jenkins_shared_lib.git']]])
                    
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
