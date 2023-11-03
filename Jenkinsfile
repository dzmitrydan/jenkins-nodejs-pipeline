pipeline {
    agent none
    tools {nodejs "node"}
    stages {
        stage('Build') {
            agent any
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
                    sh 'docker build -t nodemain:v1.0 .'
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    sh 'docker run -d --expose 3000 -p 3000:3000 nodemain:v1.0'
                }
            }
        }
    }
}