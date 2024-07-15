pipeline {
    agent any
    
    environment {
        S3_BUCKET = 'myjenkinsbucket-1'
        S3_REGION = 'us-east-2'
        S3_FILE_PATH = 'hello.txt' // File to upload
    }
    
    stages {
        stage('Upload to S3') {
            steps {
                script {
                    // Create or append content to hello.txt
                    writeFile file: S3_FILE_PATH, text: 'hello\n'
                    
                    // Upload file to S3 bucket
                    s3Upload(file: S3_FILE_PATH, bucket: S3_BUCKET, region: S3_REGION)
                }
            }
        }
    }
    
}
