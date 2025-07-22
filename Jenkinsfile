pipeline {
    agent any

    environment {
        CI = 'true'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Node.js') {
            steps {
                bat '''
                  choco install nodejs-lts -y
                  node -v
                  npm -v
                '''
            }
        }

        stage('Install dependencies') {
            steps {
                bat 'npm ci'
            }
        }

        stage('Build') {
            steps {
                bat 'npm run build || echo "No build script"'
            }
        }

        stage('Test') {
            steps {
                bat 'npm test'
            }
        }
    }
}
