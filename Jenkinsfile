pipeline {
    agent any
    
    environment {
        KUBECONFIG = credentials('kubeconfig')
    }
    
    stages {
        stage('Deploy') {
            steps {
                container('minikube') {
                    sh "kubectl --kubeconfig=$KUBECONFIG apply -f deployment.yaml"
                }
            }
        }
        // Add more stages as needed
    }
}
