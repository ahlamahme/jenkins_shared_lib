pipeline {
    agent any
    
    environment {
        KUBECONFIG_FILE = credentials('kubeconfig')
    }
    
    stages {
        stage('Apply Kubernetes Resources') {
            steps {
                withCredentials([file(credentialsId: "${KUBECONFIG_FILE}", variable: 'KUBECONFIG_FILE')]) {
                    sh "export KUBECONFIG=${KUBECONFIG_FILE} && kubectl apply -f ."
                }
            }
        }
        // Add more stages as needed
    }
    
}
