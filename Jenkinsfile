pipeline {
    agent any

    environment {
        APP_DIR = "/var/www/projects/insight/insight"
    }

    stages {

        stage('Pull Code') {
            steps {
                dir("${APP_DIR}") {
                    sh 'git pull origin main'
                }
            }
        }

        stage('Install') {
            steps {
                dir("${APP_DIR}") {
                    sh 'npm install'
                }
            }
        }

        stage('Build') {
            steps {
                dir("${APP_DIR}") {
                    sh 'npm run build'
                }
            }
        }

        stage('Restart App') {
            steps {
                sh 'pm2 restart insight-app'
            }
        }
    }
}
