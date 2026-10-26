pipeline {
    agent any
    
    triggers {
        pollSCM('* * * * *')
    }
    
    stages {
        stage('Fetch Code') {
            steps {
                checkout scm
            }
        }
        
        stage('Run Python App') {
            steps {
                sh 'python3 app.py'
            }
        }
    }
}
