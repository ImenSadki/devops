pipeline {
    agent any
    
    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-credentials')
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Docker Login') {
            steps {
                bat 'echo %DOCKERHUB_CREDENTIALS_PSW% | docker login -u %DOCKERHUB_CREDENTIALS_USR% --password-stdin'
            }
        }
        
        // Ajoutez ici vos autres stages (build, test, deploy, etc.)
    }
    
    post {
        always {
            bat 'docker logout'
        }
    }
}
