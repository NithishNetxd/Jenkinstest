pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    s3Upload(
                        profileName: 'Jenkinstest',
                        entries: [
                            [
                                bucket: 'jenkinstestbucket3',
                                sourceFile: '**/*',
                                selectedRegion: 'us-east-1',
                                storageClass: 'STANDARD',
                                uploadFromSlave: false,
                                useServerSideEncryption: false,
                                flatten: false,
                                gzipFiles: false,
                                keepForever: false,
                                showDirectlyInBrowser: false
                            ]
                        ],
                        userMetadata: [
                            [
                                key: 'BuildNumber',
                                value: env.BUILD_NUMBER
                            ]
                        ],
                        dontWaitForConcurrentBuildCompletion: false,
                        consoleLogLevel: 'INFO',
                        pluginFailureResultConstraint: 'FAILURE',
                        dontSetBuildResultOnFailure: false
                    )
                }
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
// }

