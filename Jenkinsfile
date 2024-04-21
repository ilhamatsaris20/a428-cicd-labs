node {
    stage('Build') {
        docker.image('node:16-buster-slim').withRun('-p 3200:3200') {
            sh 'npm install'
        }
    }
    stage('Test') {
        docker.image('node:16-buster-slim').withRun('-p 3200:3200') {
            sh './jenkins/scripts/test.sh'
        }
    }
    stage('Deploy') {
        docker.image('node:16-buster-slim').withRun('-p 3200:3200') {
                sh './jenkins/scripts/deliver.sh' 
                input message: 'Sudah selesai menggunakan React App? (Klik "Proceed" untuk mengakhiri)' 
                sh './jenkins/scripts/kill.sh' 
            }
        }
}
