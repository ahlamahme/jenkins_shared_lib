pipeline {
    agent any
    
    stages {
        stage('Build and Push Docker Image') {
            steps {
                // Use withCredentials block to access Docker Hub credentials
                withCredentials([usernamePassword(credentialsId: 'DuckerHub', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                    // Execute Docker commands here
                    sh "docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD"
                    sh "docker build -t ahlamahmed/flask:latest ."
                    sh "docker push ahlamahmed/flask:latest"
                }
            }
        }
        
        stage('Deploy to Minikube') {
            steps {
                // Start Minikube
                sh "minikube start"
                
                // Apply Kubernetes deployment manifest
                sh "kubectl apply -f deployment.yaml"
            }
        }
    }
}
