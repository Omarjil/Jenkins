pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello depuis un pipeline déclaratif'
            }
        }

        stage('Infos environnement') {
            steps {
                echo "Nom du noeud Jenkins: ${env.NODE_NAME}"
                echo "Workspace: ${env.WORKSPACE}"
            }
        }

        stage('Installation des dépendances') {
            steps {
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Lancement des tests') {
            steps {
                bat 'pytest'
            }
        }
    }
}