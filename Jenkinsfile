pipeline {
    agent any

    stages {
        stage('Pull Git Repository') {
            steps {
                sh 'echo pull git repository'
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