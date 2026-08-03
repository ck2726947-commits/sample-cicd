pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'python -m pytest'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t sample-cicd .'
            }
        }

        stage('Deploy Container') {
            steps {
                bat 'docker rm -f sample-cicd || exit 0'
                bat 'docker run -d --name sample-cicd sample-cicd'
            }
        }
    }
}