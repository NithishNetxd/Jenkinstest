stages {
        stage('Build') {
            steps {
                script {
                    withAWS(region: 'us-east-1', profile: 'Jenkinstest') {
                        s3Upload(
                            bucket: 'jenkinstestbucket3',
                            entries: [
                                [$class: 'hudson.plugins.s3.Entry',
                                 sourceFile: '**/*',
                                 selectedRegion: 'us-east-1',
                                 storageClass: 'STANDARD',
                                 uploadFromSlave: false,
                                 useServerSideEncryption: false,
                                 flatten: false,
                                 gzipFiles: false,
                                 keepForever: false,
                                 showDirectlyInBrowser: false]
                            ]
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
// }

