pipeline {
    environment {
        registry = "joh47/hackathon-demo"
        registryCredential = "dockerhub"
    }
    agent {
        docker { image 'node:14-alpine' }
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