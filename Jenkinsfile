pipeline {
    agent any
    
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
