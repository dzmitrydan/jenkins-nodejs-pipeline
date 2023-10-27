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
                    sh 'echo build'
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