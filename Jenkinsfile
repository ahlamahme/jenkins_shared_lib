pipeline {
    agent any
    
    environment {
        KUBECONFIG = credentials('kubeconfig')
    }
    
    stages {
        stage('Apply Deployment') {
            steps {
                container('kubectl') {
                    sh "kubectl --kubeconfig=$KUBECONFIG apply -f deployment.yaml"
                }
            }
        }
        // Add more stages as needed
    }
}
