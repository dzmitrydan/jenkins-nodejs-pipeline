pipeline {
    agent any
    tools {nodejs "node"}
    stages {
        stage('Build') {
            steps {
                sh 'node -v'
                sh 'npm -v'
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'npm test'
            }
        }
        stage('Docker build') {
            steps {
                script {
                    sh 'docker -v'
                    sh 'docker build -t nodemain:v1.0 .'
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    sh 'echo deploy'
                }
            }
        }
    }
}