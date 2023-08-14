pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub')
    }
    stages {
        stage ('Build Image') {
            steps {
                sh 'docker build -t priya20xenonstack/httpd-test .'
            }
        }
        stage ('hub login') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage ('Image Push') {
            steps {
                sh 'docker push priya20xenonstack/httpd-test'
            }
        }
    }
    post {
       always {
           sh 'docker logout'
       } 
    }
}

