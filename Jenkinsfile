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
            zip zipFile: 'deploy.zip', archive: false, dir: 'test'
            archiveArtifacts artifacts: 'deploy.zip'
          }   
        }
        
    }
}
