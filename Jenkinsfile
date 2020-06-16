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
                                        execCommand: "curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash"
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
