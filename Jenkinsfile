pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    sh 'echo "hello" >> hello.txt'
                    echo 'Building...'
                    s3Upload(
                        bucket: 'jenkinstestbucket3',
                        file: 'hello.txt',
                        path: '',
                        profile: 'Jenkinstest'
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

// s3Upload consoleLogLevel: 'INFO', dontSetBuildResultOnFailure: false, dontWaitForConcurrentBuildCompletion: false, entries: [[bucket: 'jenkinstestbucket3', excludedFile: '', flatten: false, gzipFiles: false, keepForever: false, managed Artifacts: false, noUploadOnFailure: false, selectedRegion: 'us-east-1', showDirectlyInBrowser: false, sourceFile: '**/*', storageClass: 'STANDARD'uploadFromSlave: false, useServerSide Encryption: false]], pluginFailureResultConstraint: 'FAILURE', profileName: 'Jenkinstest', userMetadata: []