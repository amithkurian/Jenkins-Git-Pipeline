pipeline {
    agent any

    environment {
        DIRECTORY_PATH = 'C:\\Users\\amith\\OneDrive\\Desktop\\2024\\t2\\223\\Jenkins\\Git'
        TESTING_ENVIRONMENT = 'TestEnv'
        PRODUCTION_ENVIRONMENT = 'AmithProd'
        EMAIL_RECIPIENT = 'amithkurian16@gmail.com'
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
            post {
                always {
                    script {
                        def logFile = "${env.WORKSPACE}/unit-integration-tests-log.txt"
                        writeFile file: logFile, text: currentBuild.rawBuild.getLogFile().text
                        archiveArtifacts artifacts: 'unit-integration-tests-log.txt'

                        mail to: "${env.EMAIL_RECIPIENT}",
                             subject: "Unit & Integration Tests: ${currentBuild.currentResult}",
                             body: """The Unit and Integration Tests stage has finished with status: ${currentBuild.currentResult}.

Please find the attached logs for more details.""",
                             attachmentsPattern: "${logFile}" // Attach log explicitly with full path
                    }
                }
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
            post {
                always {
                    script {
                        def logFile = "${env.WORKSPACE}/security-scan-log.txt"
                        writeFile file: logFile, text: currentBuild.rawBuild.getLogFile().text
                        archiveArtifacts artifacts: 'security-scan-log.txt'

                        mail to: "${env.EMAIL_RECIPIENT}",
                             subject: "Security Scan: ${currentBuild.currentResult}",
                             body: """The Security Scan stage has finished with status: ${currentBuild.currentResult}.

Please find the attached logs for more details.""",
                             attachmentsPattern: "${logFile}" // Attach log explicitly with full path
                    }
                }
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
                // Save the full log file to the workspace
                def logFile = "${env.WORKSPACE}/build-log.txt"
                writeFile file: logFile, text: currentBuild.rawBuild.getLogFile().text
                
                // Archive the log file
                archiveArtifacts artifacts: 'build-log.txt'
                
                mail to: "${env.EMAIL_RECIPIENT}",
                     subject: "Pipeline Completed: ${currentBuild.fullDisplayName}",
                     body: """The pipeline has finished.

Please find the attached logs for the full build.""",
                     attachmentsPattern: "${logFile}" // Attach full build log explicitly with full path
            }
        }
    }
}
