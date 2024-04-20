pipeline {
    agent {
        kubernetes {
            cloud 'kubernetes'
            label 'jenkins'
            defaultContainer 'jnlp'
        }
    }
    
    environment {
        KUBECONFIG = credentials('kubeconfig')
    }
    
    stages {
        stage('Deploy') {
            steps {
                container('kubectl') {
                    sh "kubectl --kubeconfig=$KUBECONFIG apply -f deployment.yaml"
                }
            }
        }
        // Add more stages as needed
    }
}
