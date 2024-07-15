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
                    echo "hello" >> hello.txt
                    s3Upload(file: S3_FILE_PATH, bucket: S3_BUCKET)
                }
            }
        }
    }
    
    post {
        always {
            // Clean up or additional actions after upload (if needed)
        }
    }
}
