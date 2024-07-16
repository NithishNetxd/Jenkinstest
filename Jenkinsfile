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
            def ZIP_FILENAME = "${JOB_NAME}_`date +%Y%m%d%H%M%S`.zip"
            sh 'touch main.txt'
            sh "zip -r $ZIP_FILENAME * "
            
            withAWS(region: 'us-east-2', credentials: 'JenkinsS3') {
                s3Upload(
                    bucket: 'jenkinsbuildbuc',
                
				    file: ZIP_FILENAME,
                    path: 'Billpay_Connector/'
                )
            }
            }
        }
    }
}
