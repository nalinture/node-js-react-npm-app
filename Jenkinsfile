pipeline {
    agent any 
        tools {
            nodejs '20.4.0'
        }

    stages {
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm -v'
            }
        }
        stage('Test') {
            steps {
                sh 'chmod +x -R ${WORKSPACE}/scripts/test.sh'
                sh './scripts/test.sh'
            }
        }
        stage('Deliver') {
            steps {
                sh 'chmod +x -R ${WORKSPACE}/scripts/deliver.sh'
                sh './scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh 'chmod +x -R ${WORKSPACE}/scripts/kill.sh'
                sh './scripts/kill.sh'
            }
        }
    }
}
