pipeline {
    agent any
    stages {
        stage('Git Checkout') {
            steps {
                script {
                    git branch: 'main', credentialsId: '3ffa1bf6-3dd0-47fd-b1fe-aa7fc54abccb', url: 'https://github.com/anasaljboor/Orange.git' 
     
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    sh 'docker build -t anasaljboor/anas:v2'
                }
            }
        }
        stage('Run') {
            steps {
                script {
                    sh 'docker run -d anasaljboor/anas:v2'
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    sh 'docker push anasaljboor/anas:v2'
                }
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                script {
                    sh 'kubectl apply -f deployments.yml'
                }
            }
        }
    }
}

