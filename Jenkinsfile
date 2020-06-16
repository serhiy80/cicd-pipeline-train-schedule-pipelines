pipeline {
    agent any
    stages {
        stage('Staging') {
            steps {
                    sshPublisher(
                        failOnError: true,
                        continueOnError: false,
                        publishers: [
                            sshPublisherDesc(
                                configName: 'dev',
                                transfers: [
                                    sshTransfer(
                                        sourceFiles: '**/*.*',
                                        excludes: 'data/**',
                                        remoteDirectory: '/tmp/temp1',
                                        execCommand: "sudo yum install -y gcc gcc-c++ make openssl-devel git; curl --silent --location https://rpm.nodesource.com/setup_10.x | sudo bash -; sudo yum install -y nodejs"
                                    ),
                                ]
                            )
                        ]
                    )
            }        
        }
        stage('Clean') {
          steps {  
            cleanWs()
          }    
        }       
    }
}
