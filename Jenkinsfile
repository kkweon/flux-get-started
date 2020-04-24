pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'env'
                sh 'docker --version'
            }
        }
        stage('Test') {
            steps {
                echo 'hello'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
