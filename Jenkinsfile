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
            // Add post-build success actions (e.g., notifications)
        }

        failure {
            echo 'Pipeline failed! Sending notifications...'
            // Add post-build failure actions (e.g., notifications)
        }

        always {
            echo 'Cleaning up...'
            // Add cleanup actions that should run regardless of success or failure
        }
    }
}
