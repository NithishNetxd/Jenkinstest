pipeline{
    agent any

    stages{
        stage("Aws Test Upload"){
            steps{
                withAWS(credentials: 'awscredentails', region: 'us-east-2'){
                    sh 'echo "Hello DevOps" > hello.txt'
                    s3Upload (acl: 'Private' , bucket: 'myjenkinsbucket-1' , file: 'hello.txt')
                    s3Download(file:'downloaded.txt', bucket:'myjenkinsbucket-1', path:'hello.txt',force:true) 
                    sh "cat downloaded.txt"

                }
            }
        }
    }
}
