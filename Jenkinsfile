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

        // Other stages...

    }

    post {
        always {
            script {
                // Save the log file to the workspace
                def logFile = "${env.WORKSPACE}/build-log.txt"
                writeFile file: logFile, text: currentBuild.rawBuild.getLogFile().text
                
                // Archive the log file
                archiveArtifacts artifacts: 'build-log.txt'
                
                // Send email with a link to the archived log
                mail to: 'amithkurian16@gmail.com',
                     subject: "Pipeline Completed: ${currentBuild.fullDisplayName}",
                     body: """The pipeline has finished.

Please access the full build log here: ${env.BUILD_URL}artifact/build-log.txt
"""
            }
        }
    }
}
