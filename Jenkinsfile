pipeline {
    agent any

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
                        // Remove profileName and region parameters as credentials are managed in the system configuration
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
