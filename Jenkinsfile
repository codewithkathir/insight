pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/codewithkathir/insight.git'
            }
        }

        stage('Install') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                rm -rf /var/www/projects/insight/insight/*
                cp -r * /var/www/projects/insight/insight

                cd /var/www/projects/insight/insight
                pm2 restart insight-app || pm2 start npm --name "insight-app" -- start
                '''
            }
        }
    }
}
