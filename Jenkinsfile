node {
    def myContainer = docker.image('node:16-buster-slim').withRun('-p 3000:3000') 

    try {
        stage('Checkout') {
            checkout scm
        }

        stage('Build') {
            myContainer.inside {
                sh 'npm install'
            }
        }
    } finally {
        myContainer.stop()
    }
}

