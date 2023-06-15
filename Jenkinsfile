pipeline {
    agent any
    environment {
        CI = 'true'
    }
    
    triggers {
        pollSCM('* * * * *')
    }
    
    stages {
        stage('Auto-monitoring') {
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
        
        stage('Tests unitaires') {
            steps {
                sh 'npm test'
            }
        }
        
        stage('Analyse statique du code') {
            steps {
                sh 'sonar-scanner'
            }
        }
        
        stage('Démarrage') {
            steps {
                sh 'npm start'
            }
        }
    }
    
    post {
        success {
            emailext(
                subject: 'Build réussi',
                body: 'Le build a réussi. Vous pouvez maintenant procéder au déploiement.',
                to: 'kmiha.anas.ra@gmail.com'
            )
        }
        
        failure {
            emailext(
                subject: 'Échec du build',
                body: 'Le build a échoué. Veuillez vérifier les logs Jenkins pour plus d\'informations.',
                to: 'kmiha.anas.ra@gmail.com'
            )
        }
    }
}
