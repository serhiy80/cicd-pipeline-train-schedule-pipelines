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
              archiveArtifacts artifacts: '**', onlyIfSuccessful: true 
              script{
                    zip archive: true, dir: 'views', glob: '', zipFile: 'deploy.zip'
                }  
          }   
        }
        
    }
}
