pipeline {
    agent any
    tools {nodejs "node"}
    stages {
        stage('Build') {
            steps {
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
                    sh 'docker build'
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    sh 'deploy'
                }
            }
        }
    }
}