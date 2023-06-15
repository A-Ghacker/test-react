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
        
        stage('Démarrage') {
            steps {
                sh 'npm start'
            }
        }
    }
    
    post {
        success {
            emailext(
                sujet: 'Build réussi',
                corps: 'Le build a réussi. Vous pouvez maintenant procéder au déploiement.',
                destinataires: 'kmiha.anas.ra@gmail.com'
            )
        }
        
        failure {
            emailext(
                sujet: 'Échec du build',
                corps: 'Le build a échoué. Veuillez vérifier les logs Jenkins pour plus d\'informations.',
                destinataires: 'votre-email@example.com'
            )
        }
    }
}
