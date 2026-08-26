
pipeline {
    agent {
        label 'agent-1'
    }
    options {
        timeout( time: 1 , unit: 'HOURS' )
        disableConcurrentBuilds()
        ansiColor('xterm')
    }
    stages {
        stage('Install Dependencies') {
            steps {
                sh """
                npm install
                """
            }
        }
        
    }
    post {
        always {
            echo "it will run always"
            deleteDir()
        }
        success {
            echo "it will run when the pipeline is success"
        }
         failure {
            echo "it will run when pipeline is failure"
        }
    }
    
}