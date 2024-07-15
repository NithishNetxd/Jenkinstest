pipeline {
    agent any

    
    stages {
        stage("AWS S3 Operations") {
            steps {
                script {
                    withAWS(region: 'us-east-2', profile: 'Upload Build to S3') {
                        // Upload a file to S3
                        sh 'echo "Hello DevOps" > hello.txt'
                        s3Upload(acl: 'Private', bucket: 'myjenkinsbucket-1', file: 'hello.txt')

                        // Download a file from S3
                        s3Download(file: 'downloaded.txt', bucket: 'myjenkinsbucket-1', path: 'hello.txt', force: true)

                        // Display the contents of the downloaded file
                        sh "cat downloaded.txt"
                    }
                }
            }
        }
    }
}
