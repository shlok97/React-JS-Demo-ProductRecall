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
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[url: 'https://github.com/appsdemo/React-JS-Demo-ProductRecall.git']]])
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
