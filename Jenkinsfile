pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                archiveArtifacts artifacts: '**', excludes: 'routes/*.*'
            }
        }
        
    }
}
