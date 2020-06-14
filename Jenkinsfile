pipeline {
    agent any

    stages {
        stage('Clean') {
          steps {  
            cleanWs()
          }    
        }
        stage('Checkout') {
          steps {  
            checkout scm
          }    
        }
        stage('Build') { 
          steps {  
              archiveArtifacts artifacts: 'gradle/wrapper/gradle-wrapper.jar, routes/index.js, test/index.test.js'
          }   
        }
        stage('Staging') {
            when {
                branch 'master'
            }
            steps {
                    sshPublisher(
                        failOnError: true,
                        continueOnError: false,
                        publishers: [
                            sshPublisherDesc(
                                configName: 'dev',
                                transfers: [
                                    sshTransfer(
                                        sourceFiles: 'gradle/wrapper/gradle-wrapper.jar',
                                        removePrefix: 'gradle/wrapper/',
                                        remoteDirectory: '/'
                                    ),
                                    sshTransfer(
                                        sourceFiles: 'routes/index.js',
                                        removePrefix: 'routes/',
                                        remoteDirectory: '/'
                                    ),
                                    sshTransfer(
                                        sourceFiles: 'test/index.test.js',
                                        removePrefix: 'test/',
                                        remoteDirectory: '/'
                                    ),
                                ]
                            )
                        ]
                    )
            }        
        }
    }
}
