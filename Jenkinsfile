pipeline {
    agent none
    stages {
        stage('Docker build') {
            steps {
                script {
                    sh 'echo "Docker build"'
                    sh 'docker -v'
                    sh 'sudo service docker status'
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