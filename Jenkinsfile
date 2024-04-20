pipeline {
    agent {
        kubernetes {
            cloud 'kubernetes'
            label 'jenkins-agent'
            containerTemplate {
                name 'kubectl'
                image 'lachlanevenson/k8s-kubectl'
                command 'cat'
                tty true
            }
        }
    }
    stages {
        stage('Apply Deployment') {
            steps {
                container('kubectl') {
                    sh "kubectl apply -f deployment.yaml"
                }
            }
        }
        // Add more stages as needed
    }
}
