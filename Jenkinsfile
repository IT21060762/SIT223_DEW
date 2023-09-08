pipeline {
    agent any

    environment {
        DIRECTORY_PATH = "/path/to/code"
        TESTING_ENVIRONMENT = "Jenkins"
        PRODUCTION_ENVIRONMENT = "Dewmith Wishmitha"
        RECIPIENT_EMAIL = "dewmithwishmitha01@gmail.com" // to send email
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
                    
                        mail to: "dewmithwishmitha01@gmail.com",
                        subject: "Test Stage Passed",
                        body: "Test stage passed successfully.",
                        attachLog: true
                    
                }
                failure {
                        mail to: "dewmithwishmitha01@gmail.com",
                        subject: "Test Stage Failed",
                        body: "Test stage failed. Please check the logs for details.",
                        attachLog: true
                
                }
            }
        }
        stage('Code Quality Check') {
            steps {
                echo "Checking the quality of the code"
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
                    post {
                    success {
                        
                            mail  to: "dewmithwishmitha01@gmail.com",
                            subject: "Test Stage Passed",
                            body: "Scan stage passed successfully.",
                            attachLog: true
                        
                    }
                    failure {
                            mail to: "dewmithwishmitha01@gmail.com",
                            subject: "Test Stage Failed",
                            body: "Scan stage failed. Please check the logs for details.",
                            attachLog: true
                    
                    }
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
