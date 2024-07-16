pipeline {
    agent any
    stages {
        stage('Upload to S3') {
            steps {
                sh 'echo "hello" >> hello.txt'
                s3Upload bucket: 'myjenkinsbucket-1',
                         region: 'us-east-2',
                         includePathPattern: 'hello.txt'
            }
        }
    }
}
