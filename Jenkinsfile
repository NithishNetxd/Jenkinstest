pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    def artifacts = [
                        [bucket: 'jenkinstestbucket3', sourceFile: '**/*', selectedRegion: 'us-east-1']
                    ]
                    s3Upload(
                        artifacts: artifacts,
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


