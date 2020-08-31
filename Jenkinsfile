pipeline {
    environment {
        registry = "joh47/hackathon-demo"
        registryCredential = "dockerhub"
    }
    agent {
        any
    }
    stages {
        stage('Build') {
            steps {
                script {
                    docker.build registry + ":latest"
                }
            }
        }
    }
}