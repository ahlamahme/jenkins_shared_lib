pipeline {
    agent any
    
    environment {
        DOCKER_USERNAME = credentials('docker-username')
        DOCKER_PASSWORD = credentials('docker-password')
        DOCKER_REGISTRY = 'https://hub.docker.com/repository/docker/ahlamahmed/flask'
        DOCKER_IMAGE_NAME = 'flask'
    }
    
    stages {
        stage('Login to Docker') {
            steps {
                sh "docker login -u ${DOCKER_USERNAME} -p ${DOCKER_PASSWORD}"
            }
        }
        
        stage('Build Docker Image') {
            steps {
                sh "docker build -t ${DOCKER_IMAGE_NAME} -f Dockerfile ."
            }
        }
        
        stage('Tag Docker Image') {
            steps {
                sh "docker tag ${DOCKER_IMAGE_NAME} ${DOCKER_REGISTRY}/${DOCKER_IMAGE_NAME}"
            }
        }
        
        stage('Push Docker Image') {
            steps {
                sh "docker push ${DOCKER_REGISTRY}/${DOCKER_IMAGE_NAME}"
            }
        }
    }
}
