pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/meerali2/node-jenkins-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run App') {
            steps {
                // You can use pm2 for production-like run
                sh 'npm install -g pm2'
                sh 'pm2 delete all || true'
                sh 'pm2 start app.js --name jenkins-app'
            }
        }
    }

    post {
        success {
            echo 'App deployed successfully!'
        }
        failure {
            echo 'App deployment failed!'
        }
    }
}
