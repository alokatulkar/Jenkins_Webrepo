pipeline {
    agent any

    environment {
        DEPLOY_DIR = "/var/www/html"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/alokatulkar/Jenkins_Webrepo.git'
            }
        }

        stage('Verify Files') {
            steps {
                sh '''
                echo "Listing files..."
                ls -la
                '''
            }
        }

        stage('Deploy to Apache') {
            steps {
                sh '''
                echo "Deploying website to Apache directory..."
                sudo rm -rf $DEPLOY_DIR/*
                sudo cp -r *.html $DEPLOY_DIR/
                sudo cp -r *.css $DEPLOY_DIR/
                '''
            }
        }

        stage('Restart Apache') {
            steps {
                sh '''
                sudo systemctl restart apache2
                '''
            }
        }
    }

    post {
        success {
            echo 'Website Deployed Successfully on Ubuntu!'
        }
        failure {
            echo 'Deployment Failed!'
        }
    }
}
