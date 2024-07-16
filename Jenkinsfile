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
                def ZIP_FILENAME = "${JOB_NAME}_${env.BUILD_ID}.zip" // Using BUILD_ID for timestamped uniqueness
                sh "echo $ZIP_FILENAME"
                sh "zip -r $ZIP_FILENAME *"
                
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
