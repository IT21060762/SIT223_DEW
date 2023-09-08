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
                        mail to: "dinukshal@gmail.com",
                        subject: "Test Stage - Success",
                        body: "The Test stage has completed successfully."

                }
            }
        }
        stage('Code Quality Check') {
            steps {
                echo "Checking the quality of the code"
            }
            post {
                //this my comment
                success {
                        mail to: "dinukshal@gmail.com",
                        subject: "Scanning Stage - Success",
                        body: "The Scanning stage has completed successfully."

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
