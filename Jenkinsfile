pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'echo "hello" >> hello.txt'
                echo 'Building...'
            }
        }
    }

    post {
        success {
            script {
                stage('Upload to S3') {
                    steps {
                        withAWS(region: 'us-east-1', credentials: 'awscredentials') {
                            s3Upload(
                                bucket: 'jenkinstestbucket3',
                                file: 'hello.txt',
                                path: ''
                            )
                        }
                    }
                }
            }
        }

        always {
            echo 'Cleaning up...'
        }
    }
}
