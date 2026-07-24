pipeline {
    agent any

   environment {
    DOCKERHUB_CREDS = credentials('dockerhub')
    DOCKERHUB_USER  = "${DOCKERHUB_CREDS_USR}"
    INDEX_NO        = '1234567890'
}

    stages {
        stage('Pull Git Repository') {
            steps { git branch: 'main', url: 'https://github.com/YThanaProton/learn-cicd.git' }
        }
        stage('Build Docker Images') {
            steps {
                sh 'docker build -f backend2/DOCKERFILE  -t $DOCKERHUB_USER/${INDEX_NO}-backend:latest  ./backend2'
                sh 'docker build -f frontend2/DOCKERFILE -t $DOCKERHUB_USER/${INDEX_NO}-frontend:latest ./frontend2'
            }
        }
        stage('Push to Docker Hub') {
            steps {
                sh 'echo $DOCKERHUB_CREDS_PSW | docker login -u $DOCKERHUB_CREDS_USR --password-stdin'
                sh 'docker push $DOCKERHUB_USER/${INDEX_NO}-backend:latest'
                sh 'docker push $DOCKERHUB_USER/${INDEX_NO}-frontend:latest'
            }
        }
    }
       post {
        always  { sh 'docker logout || true' }
        success { echo 'Images built and pushed to Docker Hub.' }
        failure { echo 'Pipeline failed. Check stage logs.' }
    }
}
