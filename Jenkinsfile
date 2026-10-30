
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t row1-laravel:${BUILD_NUMBER} .'
            }
        }

        stage('Validate Docker Compose') {
            steps {
                sh 'docker compose config --quiet'
            }
        }
    }

    post {
        success {
            echo 'Laravel Docker build completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the console output.'
        }
    }
}
