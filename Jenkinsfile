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
        always {
            script {
                withAWS(region: 'us-east-2', credentials: 'JenkinsS3') {
                    s3Upload(
                        bucket: 'jenkinsbuildbuc',
                        file: 'hello.txt',
                        path: ''
                    )
                }
                echo 'Cleaning up...'
            }
        }
    }
}
