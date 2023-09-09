pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Pull Docker Image') {
            steps {
                script {
                    sh 'docker pull anasaljboor/anas:v2'
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
        stage('Test') {
            steps {
                echo 'Running tests..'
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

