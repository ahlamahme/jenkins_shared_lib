pipeline {
    agent {
        kubernetes {
            label 'jenkins'
            defaultContainer 'jnlp'
            yaml """
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: kubectl
    image: lachlanevenson/k8s-kubectl
    command:
    - cat
"""
        }
    }
    
    stages {
        stage('Apply Deployment') {
            steps {
                container('kubectl') {
                    withCredentials([file(credentialsId: 'kubeconfig', variable: 'KUBECONFIG_FILE')]) {
                        sh "kubectl apply -f deployment.yaml --kubeconfig=$KUBECONFIG_FILE"
                    }
                }
            }
        }
        // Add more stages as needed
    }
}
