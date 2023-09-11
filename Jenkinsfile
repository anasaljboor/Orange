pipeline {
    agent any
    stages {
        stage('Git Checkout') {
            steps {
                script {
                    git branch: 'main', credentialsId: '53be62b7-ea77-4c19-a4c1-1b58ec4eb929', url: 'https://github.com/anasaljboor/Orange.git' 
     
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

