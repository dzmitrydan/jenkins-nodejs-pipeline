pipeline {
    //agent any
    agent {label "docker-agent"}
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
                    sh 'echo "Docker build"'
                    sh 'docker -v'
                    sh 'sudo service docker status'
                    //sh 'docker build -t nodemain:v1.0 .'
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    sh 'echo deploy'
                    sh 'curl http://ec2-13-51-193-237.eu-north-1.compute.amazonaws.com:4243/version'
                }
            }
        }
    }
}