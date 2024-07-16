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
            sh "zip -r Billpay_Connector.zip  * "
            
            withAWS(region: 'us-east-2', credentials: 'JenkinsS3') {
                s3Upload(
                    bucket: 'jenkinsbuildbuc',
				    file: 'Billpay_Connector.zip',
                    path: 'Billpay_Connector/'
                )
            }
            }
        }
    }
}
