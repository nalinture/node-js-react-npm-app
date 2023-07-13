pipeline {
    agent any 
        tools {
            nodejs '20.4.0'
        }

    stages {
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm --version'
            }
        }
        stage('Test') {
            steps {
                sh './scripts/test.sh'
            }
        }
        stage('Deliver') {
            steps {
                sh './scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './scripts/kill.sh'
            }
        }
    }
}
