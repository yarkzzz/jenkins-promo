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
                sudo sh './scripts/test.sh'
            }
        }
        stage('Deliver') {
            steps {
                sudo sh './scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sudo sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
