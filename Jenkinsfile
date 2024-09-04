pipeline {
    agent any

    stages {
        stage('Create Test File') {
            steps {
                script {
                    // Manually create a simple test file
                    def testFile = "${env.WORKSPACE}/test-file.txt"
                    writeFile file: testFile, text: "This is a test file for attachment."
                    
                    // Check if the file was created
                    if (fileExists(testFile)) {
                        echo "Test file created successfully at: ${testFile}"
                        
                        // Send the email with the test file attached
                        emailext(
                            to: 'amithkurian16@gmail.com',
                            subject: "Pipeline Test - File Attachment",
                            body: "This is a test email with a simple file attached.",
                            attachmentsPattern: 'test-file.txt'
                        )
                    } else {
                        echo "Failed to create the test file."
                    }
                }
            }
        }
    }
}
