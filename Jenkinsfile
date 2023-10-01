// Declarative //
pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('tiennd124-dockerhub')
    }
    stages {
        stage('Initialize') {
                def dockerHome = tool 'myDocker'
                env.PATH = "${dockerHome}/bin:${env.PATH}"
            }
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