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
          }   
        }
        
    }
}
