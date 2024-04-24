


// @Library('push_deploy') _

// pipeline {
//     agent any
    
//     stages {
//         stage('Build and Push Docker Image') {
//             steps {
//                 script {
//                     // Call the function from the shared library to build and push Docker image
//                     push_deploy.buildAndPushDockerImage('DuckerHub')
//                 }
//             }
//         }
        
//         stage('Apply Kubernetes Resources') {
//             steps {
//                 script {
//                     // Call the function from the shared library to apply Kubernetes resources
//                     push_deploy.applyKubernetesResources('kubeconfig')
//                 }
//             }
//         }
//     }
// }

@Library('push_deploy') _

pipeline {
    agent any
    
    parameters {
        string(name: 'DOCKER_IMAGE_NAME', defaultValue: 'ahlamahmed/flask', description: 'Docker image name')
        string(name: 'KUBECONFIG_CREDENTIALS_ID', defaultValue: 'kubeconfig', description: 'Credentials ID for Kubernetes config')
        string(name: 'DOCKER_CREDENTIALS_ID', defaultValue: 'DuckerHub', description: 'Credentials ID for Docker Hub')
    }
    
    stages {
        stage('Build and Push Docker Image') {
            steps {
                script {
                    // Call the function from the shared library to build and push Docker image
                    push_deploy.buildAndPushDockerImage(params.DOCKER_CREDENTIALS_ID, params.DOCKER_IMAGE_NAME)
                }
            }
        }
        
        stage('Apply Kubernetes Resources') {
            steps {
                script {
                    // Call the function from the shared library to apply Kubernetes resources
                    push_deploy.applyKubernetesResources(params.KUBECONFIG_CREDENTIALS_ID, params.DOCKER_IMAGE_NAME)
                }
            }
        }
    }
    
    post {
        success {
            echo "Pipeline succeeded"
        }
        failure {
            echo "Pipeline failed"
        }
    }
}
