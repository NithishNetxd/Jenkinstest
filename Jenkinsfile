pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    sh 'echo "hello" >> hello.txt'
                    echo 'Building...'
                }
            }
        }
    }

    post {
        success {
            script {
                withAWS(region: 'us-east-2', credentials: 'JenkinsS3') {
                    s3Upload(
                        bucket: 'jenkinsbuildbuc',
                        file: 'hello.txt',
                        path: 'builds/'
                    )
                }
                echo 'Cleaning up...'
            }
        }
    }
}
