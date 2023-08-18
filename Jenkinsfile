node {
    def dockerImage = 'node:16-buster-slim'
    def dockerArgs = '-p 3000:3000'

    stage('Build') {
        docker.image(dockerImage).withRun(dockerArgs) { container ->
            // Install necessary tools
            sh 'apt-get update'
            sh 'apt-get install -y nodejs npm'

            // Run npm install
            sh 'npm install'
        }
    }

    stage('Test') {
        docker.image(dockerImage).withRun(dockerArgs) { container ->
            // Install necessary tools
            sh 'apt-get update'
            sh 'apt-get install -y nodejs npm'

            // Run test script
            sh './jenkins/scripts/test.sh'
        }
    }
}



