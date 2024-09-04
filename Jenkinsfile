pipeline {
    agent any

    environment {
        EMAIL_RECIPIENT = 'amithkurian16@gmail.com'
    }

    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Building the code using Maven (e.g., mvn clean package)'
                    bat 'echo Simulated Build output > build.log'
                }
            }
            post {
                success {
                    archiveArtifacts artifacts: 'build.log'
                    emailext to: "${EMAIL_RECIPIENT}",
                             subject: "Build Successful",
                             body: "The Build stage completed successfully. Logs are attached.",
                             attachmentsPattern: "build.log"
                }
                failure {
                    archiveArtifacts artifacts: 'build.log'
                    emailext to: "${EMAIL_RECIPIENT}",
                             subject: "Build Failed",
                             body: "The Build stage failed. Logs are attached.",
                             attachmentsPattern: "build.log"
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo 'Running unit tests using JUnit and integration tests using TestNG'
                    bat 'echo Simulated Unit and Integration Tests output > unit-tests.log'
                }
            }
            post {
                success {
                    archiveArtifacts artifacts: 'unit-tests.log'
                    emailext to: "${EMAIL_RECIPIENT}",
                             subject: "Unit and Integration Tests Successful",
                             body: "The Unit and Integration Tests stage completed successfully. Logs are attached.",
                             attachmentsPattern: "unit-tests.log"
                }
                failure {
                    archiveArtifacts artifacts: 'unit-tests.log'
                    emailext to: "${EMAIL_RECIPIENT}",
                             subject: "Unit and Integration Tests Failed",
                             body: "The Unit and Integration Tests stage failed. Logs are attached.",
                             attachmentsPattern: "unit-tests.log"
                }
            }
        }

        stage('Code Analysis') {
            steps {
                script {
                    echo 'Analyzing code using SonarQube to ensure it meets industry standards'
                    bat 'echo Simulated Code Analysis output > code-analysis.log'
                }
            }
            post {
                success {
                    archiveArtifacts artifacts: 'code-analysis.log'
                    emailext to: "${EMAIL_RECIPIENT}",
                             subject: "Code Analysis Successful",
                             body: "The Code Analysis stage completed successfully. Logs are attached.",
                             attachmentsPattern: "code-analysis.log"
                }
                failure {
                    archiveArtifacts artifacts: 'code-analysis.log'
                    emailext to: "${EMAIL_RECIPIENT}",
                             subject: "Code Analysis Failed",
                             body: "The Code Analysis stage failed. Logs are attached.",
                             attachmentsPattern: "code-analysis.log"
                }
            }
        }

        stage('Security Scan') {
            steps {
                script {
                    echo 'Performing security scan using OWASP Dependency-Check'
                    bat 'echo Simulated Security Scan output > security-scan.log'
                }
            }
            post {
                success {
                    archiveArtifacts artifacts: 'security-scan.log'
                    emailext to: "${EMAIL_RECIPIENT}",
                             subject: "Security Scan Successful",
                             body: "The Security Scan stage completed successfully. Logs are attached.",
                             attachmentsPattern: "security-scan.log"
                }
                failure {
                    archiveArtifacts artifacts: 'security-scan.log'
                    emailext to: "${EMAIL_RECIPIENT}",
                             subject: "Security Scan Failed",
                             body: "The Security Scan stage failed. Logs are attached.",
                             attachmentsPattern: "security-scan.log"
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                script {
                    echo 'Deploying the application to AWS EC2 Staging server'
                    bat 'echo Simulated Deployment to Staging > deploy-staging.log'
                }
            }
            post {
                success {
                    archiveArtifacts artifacts: 'deploy-staging.log'
                    emailext to: "${EMAIL_RECIPIENT}",
                             subject: "Deployment to Staging Successful",
                             body: "The Deploy to Staging stage completed successfully. Logs are attached.",
                             attachmentsPattern: "deploy-staging.log"
                }
                failure {
                    archiveArtifacts artifacts: 'deploy-staging.log'
                    emailext to: "${EMAIL_RECIPIENT}",
                             subject: "Deployment to Staging Failed",
                             body: "The Deploy to Staging stage failed. Logs are attached.",
                             attachmentsPattern: "deploy-staging.log"
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo 'Running integration tests on the staging environment using Selenium'
                    bat 'echo Simulated Integration Tests on Staging > integration-tests-staging.log'
                }
            }
            post {
                success {
                    archiveArtifacts artifacts: 'integration-tests-staging.log'
                    emailext to: "${EMAIL_RECIPIENT}",
                             subject: "Integration Tests on Staging Successful",
                             body: "The Integration Tests on Staging stage completed successfully. Logs are attached.",
                             attachmentsPattern: "integration-tests-staging.log"
                }
                failure {
                    archiveArtifacts artifacts: 'integration-tests-staging.log'
                    emailext to: "${EMAIL_RECIPIENT}",
                             subject: "Integration Tests on Staging Failed",
                             body: "The Integration Tests on Staging stage failed. Logs are attached.",
                             attachmentsPattern: "integration-tests-staging.log"
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                script {
                    echo 'Deploying the application to AWS EC2 Production server'
                    bat 'echo Simulated Deployment to Production > deploy-production.log'
                }
            }
            post {
                success {
                    archiveArtifacts artifacts: 'deploy-production.log'
                    emailext to: "${EMAIL_RECIPIENT}",
                             subject: "Deployment to Production Successful",
                             body: "The Deploy to Production stage completed successfully. Logs are attached.",
                             attachmentsPattern: "deploy-production.log"
                }
                failure {
                    archiveArtifacts artifacts: 'deploy-production.log'
                    emailext to: "${EMAIL_RECIPIENT}",
                             subject: "Deployment to Production Failed",
                             body: "The Deploy to Production stage failed. Logs are attached.",
                             attachmentsPattern: "deploy-production.log"
                }
            }
        }
    }
}
