pipeline {
    agent any

    stages {
        stage('Clean') {
            cleanWs()
        }
        stage('Checkout') {
            checkout scm
        }
        stage('Build') {
            zip zipFile: 'deploy.zip', archive: false, dir: '**'
            archiveArtifacts artifacts: 'deploy.zip'
        }
        
    }
}
