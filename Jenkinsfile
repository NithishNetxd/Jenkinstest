pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    s3Upload(
                        entries: [
                            [bucket: 'jenkinstestbucket3', sourceFile: '**/*', selectedRegion: 'us-east-1']
                        ],
                        profileName: 'Jenkinstest'
                    )
                }
            }
        }
    }
}

    // post {
    //     always {
    //         script {
    //             withAWS(region: 'us-east-1', profile: 'Jenkinstest') {
    //                 s3Upload(
    //                     bucket: 'jenkinstestbucket3',
    //                     file: 'hello.txt',
    //                     path: ''
    //                 )
    //             }
    //             echo 'Cleaning up...'
    //         }
    //     }
    // }   


