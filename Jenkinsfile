pipeline {
    agent any

   environment {
    DOCKERHUB_CREDS = credentials('dockerhub-creds')
    DOCKERHUB_USER  = "${DOCKERHUB_CREDS_USR}"
    INDEX_NO        = '1234567890'
}

    stages {
        stage('Pull Git Repository') {
            steps {
                sh 'echo pull git repository'
                sh 'echo ${DOCKERHUB_USER}'
                sh 'echo ${DOCKERHUB_CREDS}'
            }
        }
        stage('Build Docker Images') {
            steps {
                sh 'echo build docker images'
            }
        }
        stage('Push to Docker Hub') {
            steps {
                sh 'echo push to docker hub'
            }
        }
    }
}
