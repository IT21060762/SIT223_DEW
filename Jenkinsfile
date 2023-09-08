pipeline {
    agent any

    environment {
        DIRECTORY_PATH = "/path/to/code"
        TESTING_ENVIRONMENT = "Jenkins"
        PRODUCTION_ENVIRONMENT = "Dewmith Wishmitha"
    }

    stages {
        stage('Build') {
            steps {
                echo "Fetching the source code from the directory path: ${env.DIRECTORY_PATH}"
                echo "Compiling the code and generating artifacts"
            }
        }
        stage('Test') {
            steps {
                echo "Running unit tests"
                echo "Running integration tests"
            }
            post {
                success {
                    emailext (
                        subject: 'Test Stage - Success',
                        body: 'The Test stage has completed successfully.',
                        to: 'dinukshal@gmail.com'
                    )
                }
                failure {
                    emailext (
                        subject: 'Test Stage - Failure',
                        body: 'The Test stage has failed.',
                        to: 'dinukshal@gmail.com'
                    )
                }
            }
        }
        stage('Code Quality Check') {
            steps {
                echo "Checking the quality of the code"
            }
            post {
                success {
                    emailext (
                        subject: 'Code Quality Check - Success',
                        body: 'The Code Quality Check stage has completed successfully.',
                        to: 'dinukshal@gmail.com'
                    )
                }
                failure {
                    emailext (
                        subject: 'Code Quality Check - Failure',
                        body: 'The Code Quality Check stage has failed.',
                        to: 'dinukshal@gmail.com'
                    )
                }
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying the application to testing environment: ${env.TESTING_ENVIRONMENT}"
            }
        }
        stage('Approval') {
            steps {
                script {
                    echo "Waiting for manual approval..."
                    sleep(time: 10, unit: 'SECONDS')
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying the code to production environment: ${env.PRODUCTION_ENVIRONMENT}"
            }
        }
    }
}
