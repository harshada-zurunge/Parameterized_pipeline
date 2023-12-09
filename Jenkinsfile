pipeline {
    agent any

    parameters {
        string(name: 'ENVIRONMENT', defaultValue: 'dev', description: 'Target environment (e.g., dev, staging, prod)')
    }

    environment {
        // Define environment variables
        APP_VERSION = '1.0.0'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo "Building version ${APP_VERSION} for ${params.ENVIRONMENT} environment..."
                // Add your build commands here
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Add your test commands here
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying to ${params.ENVIRONMENT} environment..."
                // Add your deployment commands here
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded! Sending notifications...'
            emailext (
                to: 'harshadazurungedevops@gmail.com', // Replace with the target email address
                subject: "Jenkins Pipeline Success - ${params.ENVIRONMENT}",
                body: "Your Jenkins pipeline has succeeded for environment: ${params.ENVIRONMENT}"
            )
        }

        failure {
            echo 'Pipeline failed! Sending notifications...'
            emailext (
                to: 'harshadazurungedevops@gmail.com', // Replace with the target email address
                subject: "Jenkins Pipeline Failure - ${params.ENVIRONMENT}",
                body: "Your Jenkins pipeline has failed for environment: ${params.ENVIRONMENT}"
            )
        }

        always {
            echo 'Cleaning up...'
            // Add cleanup actions that should run regardless of success or failure
        }
    }
}
