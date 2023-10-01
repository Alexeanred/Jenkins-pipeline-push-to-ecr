// Declarative //
pipeline {
    agent any

    stages {
        stage('Clone stage') {
            steps {
                git "https://github.com/Alexeanred/learning-docker-python-2.git"
            }
        }
        stage('Build stage') {
            steps { withDockerRegistry(credentialsId: 'docker-hub', url: 'https://index.docker.io/v1/') 
                sh 'docker build -t tiennd124/github-jenkins-repo:v1 .'
                sh 'docker push tiennd124/github-jenkins-repo:v1'
            }
        }
    }
}