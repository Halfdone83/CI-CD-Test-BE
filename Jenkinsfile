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
                sh '''
                  curl -fsSL https://deb.nodesource.com/setup_18.x | bash -
                  apt-get install -y nodejs
                  node -v
                  npm -v
                '''
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'npm ci'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build || echo "No build script"'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }
    }
}
