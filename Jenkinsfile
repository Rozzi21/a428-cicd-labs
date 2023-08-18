node {
    // Define Docker image and port mapping
    def dockerImage = 'node:16-buster-slim'
    def dockerArgs = '-p 3000:3000'

    // Stage: Build
    stage('Build') {
        // Run inside Docker container
        docker.image(dockerImage).withRun(dockerArgs) { container ->
            // Run npm install
            sh 'npm install'
        }
    }

    // Stage: Test
    stage('Test') {
        // Run inside Docker container
        docker.image(dockerImage).withRun(dockerArgs) { container ->
            // Run test script
            sh './jenkins/scripts/test.sh'
        }
    }
}



