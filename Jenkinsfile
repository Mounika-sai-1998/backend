
pipeline {
    agent {
        label 'agent-1'
    }
    options {
        timeout( time: 1 , unit: 'HOURS' )
        disableConcurrentBuilds()
        ansiColor('xterm')
    }
    environment {
        def appVersion = ''
    }
    stages {
        stage('Read Version') {
            steps {
                script {
                    def packageJson = readJSON file: 'package.json'
                    appVersion = packageJson.version
                    echo "application version : $appVersion"
                }
            }
        }
        stage('Install Dependencies') {
            steps {
                sh """
                npm install
                ls -lrt
                echo "application version : $appVersion"
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