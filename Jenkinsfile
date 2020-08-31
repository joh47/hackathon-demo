pipeline {
    environment {
        registry = "joh47/hackathon-demo"
        registryCredential = "dockerhub"
        dockerImage = ""
    }
    agent any
    stages {
        stage('SAST Scan') {
            steps {
                script {
                    sh 'docker run --rm -e "WORKSPACE=${PWD}" -v "$PWD:/app:cached" quay.io/appthreat/sast-scan scan --src /app --type python'
                }
            }
        }
        // stage('SAST Scan') {
        //     steps {
        //         script {
        //             docker.image('quay.io/appthreat/sast-scan').run('--rm -e "WORKSPACE=${PWD}" -v "$PWD:/app:cached"', 'scan --src /app --type python -o ./reports')
        //         }
        //     }
        // }
        stage('Build') {
            steps {
                script {
                    dockerImage = docker.build registry + ":latest"
                }
            }
        }
        stage('Publish Image') {
            steps{
                script {
                    docker.withRegistry( '', registryCredential ) {
                        dockerImage.push()
                    }
                }
            }
        }
    }
}