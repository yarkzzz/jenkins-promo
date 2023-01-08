pipeline {
  agent any

    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                 sh "chmod +x -R ${env.WORKSPACE}"
                 sh './scripts/test.sh'
            }
        }
        stage('Deliver') {
            steps {
                sh "chmod +x -R ${env.WORKSPACE}"
                sh './scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh "chmod +x -R ${env.WORKSPACE}"
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
