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
                    // Define the file(s) to upload and the destination bucket
                    def files = [
                        [bucket: 'jenkinstestbucket3', sourceFile: 'hello.txt', excludedFile: '', storageClass: 'STANDARD']
                    ]

                    // Upload files to S3
                    s3Upload(
                        profileName: env.PROFILE_NAME,
                        entries: files,
                        selectedRegion: 'us-east-1', // Replace with your AWS region
                        noUploadOnFailure: false,
                        uploadFromSlave: false,
                        managedArtifacts: false,
                        useServerSideEncryption: true,
                        flatten: true,
                        gzipFiles: false,
                        keepForever: false,
                        showDirectlyInBrowser: false,
                        dontWaitForConcurrentBuildCompletion: false,
                        consoleLogLevel: 'INFO'
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
