pipeline {
    agent {
        docker {
            image 'node:12-alpine'
            args '-p 8000:8000'
        }
    }
    environment {
      CI = 'true'
    }
    stages {
        stage('Pull') {
            steps {
                sh 'git pull'
            }
        }
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'npm run test'
            }
        }
        stage('Deploy') {
            steps {
                sh 'npm start'
            }
        }
    }
}
