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
          script{
                    zip archive: true, dir: 'views', glob: '', zipFile: 'deploy.zip'
                }   
          steps {  
              archiveArtifacts artifacts: '**', onlyIfSuccessful: true   
          }   
        }
        
    }
}
