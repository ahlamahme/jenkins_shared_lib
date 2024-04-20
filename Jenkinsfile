pipeline {
    agent any
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
    stages {
        stage('Apply Kubernetes Resources') {
            steps {
                withCredentials([file(credentialsId: 'kubeconfig', variable: 'KUBECONFIG_FILE')]) {
                    sh "export KUBECONFIG=${KUBECONFIG_FILE} && kubectl apply -f ."
                }
            }
        }
        // Add more stages as needed
    }
}
