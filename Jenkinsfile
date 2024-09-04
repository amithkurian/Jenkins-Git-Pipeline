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
                // Save the full log file to the workspace
                def logFile = "${env.WORKSPACE}/build-log.txt"
                writeFile file: logFile, text: currentBuild.rawBuild.getLogFile().text
                
                // Archive the log file
                archiveArtifacts artifacts: 'build-log.txt'
                
                def buildLogSnippet = currentBuild.rawBuild.getLog().join("\n")
                
                mail to: 'amithkurian16@gmail.com',
                     subject: "Pipeline Completed: ${currentBuild.fullDisplayName}",
                     body: """The pipeline has finished.

Here are the last 1000 lines of the build log:

${buildLogSnippet}

For the full log, please visit: ${env.BUILD_URL}artifact/build-log.txt
"""
            }
        }
    }
}
