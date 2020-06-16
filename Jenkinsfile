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
                                        sourceFiles: 'gradle/wrapper/gradle-wrapper.jar',
                                        removePrefix: 'gradle/wrapper/',
                                        remoteDirectory: '/tmp'
                                    ),
                                    sshTransfer(
                                        sourceFiles: 'routes/index.js',
                                        removePrefix: 'routes/',
                                        remoteDirectory: '/tmp'
                                    ),
                                    sshTransfer(
                                        sourceFiles: 'test/index.test.js',
                                        removePrefix: 'test/',
                                        remoteDirectory: '/tmp'
                                    ),
                                    sshTransfer(
                                        sourceFiles: 'bin/just_for_fun.txt',
                                        removePrefix: 'bin/',
                                        remoteDirectory: '/tmp'
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
