pipeline {
    agent any
    
    environment {
        AWS_DEFAULT_REGION = 'us-east-2'
    }
    
    stages {
        stage("AWS S3 Operations") {
            steps {
                script {
                    // Assuming credentials are globally configured, no need to specify them here
                    sh 'echo "Hello DevOps" > hello.txt'
                    
                    // Uploading file to S3
                    s3Upload(path: 'hello.txt', bucket: 'myjenkinsbucket-1', file: 'hello.txt')
                    
                    // Downloading file from S3
                    s3Download(bucket: 'myjenkinsbucket-1', file: 'hello.txt', path: 'downloaded.txt')
                    
                    // Displaying downloaded file content
                    sh "cat downloaded.txt"
                }
            }
        }
    }
}
