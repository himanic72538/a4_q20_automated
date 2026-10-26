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
        
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t himanic72538/my-flask-app:latest .'
            }
        }
        
        stage('Run Container') {
            steps {
                sh 'docker rm -f my-running-container || true'
                sh 'docker run -d --name my-running-container himanic72538/my-flask-app:latest'
            }
        }
        
        stage('Verify Container') {
            steps {
                sh 'docker ps --filter name=my-running-container'
                sh 'docker logs my-running-container'
            }
        }
    }
}
