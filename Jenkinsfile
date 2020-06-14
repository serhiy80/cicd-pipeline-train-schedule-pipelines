@Library('github.com/releaseworks/jenkinslib') _
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
          steps {
            withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: 'aws-key', usernameVariable: 'AWS_ACCESS_KEY_ID', passwordVariable: 'AWS_SECRET_ACCESS_KEY']]) {
        AWS("--region=us-east-1 s3 ls")
    }
          }
        }
    }
}
