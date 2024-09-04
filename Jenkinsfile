pipeline {
    agent any

    environment {
        DIRECTORY_PATH = 'C:\\Users\\amith\\OneDrive\\Desktop\\2024\\t2\\223\\Jenkins\\Git'
        TESTING_ENVIRONMENT = 'TestEnv'
        PRODUCTION_ENVIRONMENT = 'AmithProd'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven (e.g., mvn clean package)'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests using JUnit and integration tests using TestNG'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyzing code using SonarQube to ensure it meets industry standards'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan using OWASP Dependency-Check'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying the application to AWS EC2 Staging server'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on the staging environment using Selenium'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying the application to AWS EC2 Production server'
            }
        }
    }

     post {
        always {
            script {
                // Define the path to the log file inside the workspace
                def logFile = "${env.WORKSPACE}/pipeline-log.txt"
                
                // Write the last 1000 lines of the log to the file
                writeFile file: logFile, text: currentBuild.rawBuild.getLog(1000).join("\n")
                
                // Ensure the file was created successfully
                if (fileExists(logFile)) {
                    echo "Log file created successfully at: ${logFile}"
                    
                    // Use emailext to attach the log file
                    emailext(
                        to: 'amithkurian16@gmail.com',
                        subject: "Pipeline Completed: ${currentBuild.fullDisplayName}",
                        body: "The pipeline has finished. Please find the attached log file.",
                        attachmentsPattern: 'pipeline-log.txt'
                    )
                } else {
                    echo "Failed to create the log file."
                }
            }
        }
    }
}
