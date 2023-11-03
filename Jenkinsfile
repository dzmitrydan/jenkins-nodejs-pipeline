pipeline {
    agent none
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:7.8.0'
                }
            }
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            agent {
                docker {
                    image 'node:7.8.0'
                }
            }
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
            agent any
            steps {
                script {
                    sh 'docker run -d --expose 3001 -p 3001:3000 --rm --name nodedev nodedev:v1.0'
                }
            }
        }
    }
}