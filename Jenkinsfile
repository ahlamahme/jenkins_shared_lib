


@Library('push_deploy') _

pipeline {
    agent any
    
    stages {
        stage('Build and Push Docker Image') {
            steps {
                script {
                    // Call the function from the shared library to build and push Docker image
                    push_deploy.buildAndPushDockerImage('DuckerHub')
                }
            }
        }
        
        stage('Apply Kubernetes Resources') {
            steps {
                script {
                    // Call the function from the shared library to apply Kubernetes resources
                    push_deploy.applyKubernetesResources('kubeconfig')
                }
            }
        }
    }
}
