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
                withAWS(region: 'us-east-1', profile: 'Jenkinstest') {
                    s3Upload(
                        bucket: 'jenkinstestbucket3',
                        file: 'hello.txt',
                        path: ''
                    )
                }
                echo 'Cleaning up...'
            }
        }
    }   
}

