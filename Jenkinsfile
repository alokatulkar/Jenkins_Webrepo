pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/alokatulkar/Jenkins_Webrepo.git'
            }
        }

        stage('Verify Files') {
            steps {
                sh '''
                echo "Checking website files..."
                ls -la
                '''
            }
        }

        stage('Archive Website') {
            steps {
                archiveArtifacts artifacts: '*.html, *.css', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Website pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
