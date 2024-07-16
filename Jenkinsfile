pipeline {
    agent any

    environment {
        // Define the AWS profile to use
        PROFILE_NAME = 'Jenkinstest'
    }

    stages {
        stage('Build') {
            steps {
                sh 'echo "hello" >> hello.txt'
                echo 'Building...'
            }
        }

        stage('Upload to S3') {
            steps {
                script {
                    // Upload files to S3
                    s3Upload(
                        bucket: 'jenkinstestbucket3', 
                        file: 'hello.txt', 
                        profileName: env.PROFILE_NAME,
                        path: '', // S3 path where you want to upload the file
                        region: 'us-east-1', // Replace with your AWS region
                        includePathPattern: '**/*'
                    )
                }
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
        }
    }
}
