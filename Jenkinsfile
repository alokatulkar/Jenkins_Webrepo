pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/alokatulkar/Jenkins_Webrepo.git'
            }
        }

        stage('Verify Files') {
            steps {
                sh 'ls -la'
            }
        }

        stage('Deploy to Apache') {
            steps {
                sh '''
                rm -rf /var/www/html/*
                cp *.html /var/www/html/
                cp *.css /var/www/html/
                '''
            }
        }
    }

    post {
        success {
            echo 'Website Deployed Successfully!'
        }
        failure {
            echo 'Deployment Failed!'
        }
    }
}
