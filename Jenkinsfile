// Declarative //
pipeline {
    agent {
        docker { image 'node:18.18.0-alpine3.18' }
    }
    environment {
        DOCKERHUB_CREDENTIALS = credentials('tiennd124-dockerhub')
    }
    stages {
        stage("Build") {
            steps {
                sh 'docker build -t tiennd124/github-jenkins-repo:latest .'
            }
        }
        stage("Login") {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage("Push") {
            steps {
                sh 'docker push tiennd124/github-jenkins-repo:latest'
            }          
        }
    }
    post {
        always {
            sh 'docker logout'
        }
    }
}