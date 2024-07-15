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
                    s3Upload(bucket: 'myjenkinsbucket-1', file: 'hello.txt', path: 'hello.txt', workspace: true)
                    s3Download(bucket: 'myjenkinsbucket-1', file: 'downloaded.txt', path: 'hello.txt', flatten: true)
                    sh "cat downloaded.txt"
                }
            }
        }
    }
}
