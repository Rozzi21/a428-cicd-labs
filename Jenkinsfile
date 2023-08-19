node  {
    def dockerImage = 'node:16-buster-slim'

    stage('Build') {
        docker.image(dockerImage).inside("-p 3000:3000") {
            sh 'npm install'
        }
    }

    stage('Test') {
        docker.image(dockerImage).inside("-p 3000:3000") {
            sh './jenkins/scripts/test.sh'
        }

    }
    stage('Manual Approval') {
        input message: 'Lanjutkan ke tahap Deploy? (Klik "Proceed" untuk mengakhiri)'
    }
    stage('Deploy') {
        sh './jenkins/scripts/deliver.sh'
        echo "60 seconds for test before the app shutdown please wait :)"
        sleep 60
        sh './jenkins/scripts/kill.sh'
    }
}
