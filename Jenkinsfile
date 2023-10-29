pipeline {
  agent any
  stages {
    stage('Test') {
      steps {
        sh 'curl http://ec2-13-51-193-237.eu-north-1.compute.amazonaws.com:4243/version'
      }
    }
  }
}