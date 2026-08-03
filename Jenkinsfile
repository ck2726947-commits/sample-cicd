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
                bat 'C:\\Users\\ChetanKumar\\AppData\\Local\\Python\\bin\\python.exe -m pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'C:\\Users\\ChetanKumar\\AppData\\Local\\Python\\bin\\python.exe -m pytest'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'C:\\Users\\ChetanKumar\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe build -t sample-cicd .'
            }
        }

        stage('Deploy Container') {
            steps {
                bat 'C:\\Users\\ChetanKumar\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe run -d -p 5000:5000 sample-cicd'
            }
        }
    }
}