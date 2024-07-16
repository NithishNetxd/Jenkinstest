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
                withAWS(credentials: 'awscredentials') {
                    s3Upload(
                        bucket: 'jenkinstestbucket3',
                        file: 'hello.txt',
                        path: ''
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
