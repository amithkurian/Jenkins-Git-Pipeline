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
                def buildLog = currentBuild.rawBuild.getLog(1000).join("\n") // get the last 100 lines of the log
                mail to: 'amithkurian16@gmail.com',
                     subject: "Pipeline Completed: ${currentBuild.fullDisplayName}",
                     body: "The pipeline has finished.\n\nHere are the last 1000 lines of the build log:\n${buildLog}"
            }
        }
    }
}
