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
              script{
                    zip archive: true, dir: 'views', glob: '', zipFile: 'deploy.zip'
                }  
              archiveArtifacts artifacts: 'deploy.zip', onlyIfSuccessful: true 
          }   
        }
        
    }
}
