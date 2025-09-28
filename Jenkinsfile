pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/MnuelD/python-api.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t python-api .'
            }
        }

        stage('Run with Docker Compose') {
            steps {
                sh 'docker-compose up -d'
            }
        }
    }
}
