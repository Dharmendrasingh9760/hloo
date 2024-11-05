pipeline {
        agent any
        stages {
                stage ("pull code from github"){
                        steps{
               git branch: 'main', url: 'https://github.com/Dharmendrasingh9760/node.js.git'
                        }
                }
                stage('Remove Old Containers and Images') {
                    steps {
                      script {
                    sh '''
                    sudo docker stop node-js  || true
                    sudo docker rm node-js || true
                    '''
                    sh '''
                    sudo docker rmi node-hello:latest || true
                    '''
                }
            }
        }
               
            
                stage ("Building docker image"){
                        steps{
                                sh 'sudo docker build -t node-hello:latest .'
                        }
                }
                
                stage ("Testing the Build"){
                        steps{
                                sh 'sudo docker run -dit --name node-js -p 4001:4001 node-hello:latest'
                                
                        }
                }


        }
}
