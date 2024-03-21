pipeline {
    environment {
        registry = "azizmoubsit/tp4-devops"
        registryCredential = 'docker_azizmoubsit_jenkins'
        dockerImage = ''
    }
    agent any
    stages {
        stage('Cloning Git') {
            steps {
                git 'https://github.com/azizmoubsit/tp4-devops'
            }
        }
        stage('Building image') {
            steps{
                script {
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                }
            }
        }
        stage('Test image') {
            steps{
                script {
                    echo "Tests passed"
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