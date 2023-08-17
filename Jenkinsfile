pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    docker.image('node:16-buster-slim').inside('-p 3000:3000') {
                        sh 'npm install'
                    }
                }
            }
        }
        stage('Test') {
            steps {
                script {
                         sh './jenkins/scripts/test.sh'
                }  
            }
        }
    }
}

