pipeline {
    agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000'
        }
    }
    environment {
      CI = 'true'
    }
    stages {
        stage('Setup Node') {
            steps {
              env.NODE_HOME="${tool 'nodejs'}"
              env.PATH="${env.NODE_HOME}/bin:${env.PATH}"
              sh 'npm --version'
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
