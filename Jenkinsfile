pipeline{
    agent any
    stages{
        stage('build'){
            steps{
                script{
                    echo "Building the application"
                }
            }
        }
        stage("test"){
            steps{
                script{
                    echo "Testing the application"
                }
            }
        }
        stage("deploy"){
            steps{
                script{
                    def dockerCMD = "docker run -d -p 3000:80 mshallom/demo-app:1.0"
                    sshagent(['ec2-server-key']) {
                        sh "ssh -o StrictHostKeyChecking=no ec2-user@34.228.40.92 ${dockerCMD}"
                    }
                }
            }
        }
    }
}