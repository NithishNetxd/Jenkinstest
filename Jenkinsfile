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
                    // Upload a single file to S3
                    s3Upload(
                        bucket: 'jenkinstestbucket3',
                        file: 'hello.txt',
                        path: '', // S3 path where you want to upload the file
                        profileName: env.PROFILE_NAME,
                        region: 'us-east-1' // Replace with your AWS region
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
