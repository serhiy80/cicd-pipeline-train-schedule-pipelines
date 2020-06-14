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
            zip archive: true, dir: 'test', glob: '', zipFile: 'deploy.zip'  
            archiveArtifacts artifacts: 'deploy.zip'
          }   
        }
        
    }
}
