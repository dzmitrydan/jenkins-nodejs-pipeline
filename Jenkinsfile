pipeline {
    agent none
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
            agent any
            steps {
                script {
                    sh 'docker build -t nodedev:v1.0 .'
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    sh 'docker run -d --expose 3001 -p 3001:3000 nodedev:v1.0'
                }
            }
        }
    }
}