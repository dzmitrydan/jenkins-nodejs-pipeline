pipeline {
    agent any
    stages {
        stage('Build') {
                    steps {
                        script{
                         app = docker.build("underwater")
                        }
                    }
       }
    }
}