pipeline {
    agent {
        label 'node_jenkins'
    }
        
    environment {
        CI = 'true'
    }
    stages {
        stage('self monitoring') {
            steps {
                sh 'pwd'
                sh 'ls -alihs'
                sh 'node -v'
                sh "printenv | sort"
            }
        }
        stage('Build') {
            steps {
                sh 'npm i'
            }
        }
        stage('start'){
            steps {
                sh 'npm start'
            }
        }
        /*stage('Test') {
            steps {
                 
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
        stage('Deploy') {
            steps {
                sh './jenkins/scripts/deploy.sh'
            }
        }*/
    }
}
