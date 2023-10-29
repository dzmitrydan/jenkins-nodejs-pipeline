pipeline {
  agent {
    docker { image 'node:20.9.0-alpine' }
  }
  stages {
    stage('Test') {
      steps {
        sh 'node --version'
      }
    }
  }
}