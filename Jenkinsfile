pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-credentials') // Configurez les credentials dans Jenkins
        DOCKERHUB_USERNAME = 'votre-nom-utilisateur-dockerhub'
    }

    stages {
        stage('Cloner le dépôt') {
            steps {
                echo "Clonage du dépôt Git..."
                git branch: 'main', url: 'https://github.com/ImenSadki/devops.git'
            }
        }
        stage('Construire les images Docker') {
            steps {
                echo "Construction des images Docker..."
                sh 'docker-compose build'
            }
        }
        stage('Pousser les images Docker') {
            steps {
                echo "Push des images Docker vers Docker Hub..."
                script {
                    sh """
                    echo "$DOCKERHUB_CREDENTIALS_PSW" | docker login -u "$DOCKERHUB_USERNAME" --password-stdin
                    docker-compose push
                    """
                }
            }
        }
        stage('Déployer avec Docker Compose') {
            steps {
                echo "Déploiement des conteneurs..."
                sh 'docker-compose up -d'
            }
        }
    }

    post {
        success {
            echo "Pipeline exécuté avec succès !"
        }
        failure {
            echo "Le pipeline a échoué !"
        }
    }
}

