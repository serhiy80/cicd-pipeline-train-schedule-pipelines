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
            checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github_key', url: 'git@github.com:serhiy80/cicd-pipeline-train-schedule-pipelines.git']]])
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
                                    sshTransfer(
                                        sourceFiles: 'bin/just_for_fun.txt',
                                        removePrefix: 'bin/',
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
