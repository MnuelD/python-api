pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/MnuelD/python-api.git'
            }
        }

        stage('Test') {
            steps {
                bat '''
                    python -m pip install --upgrade pip
                    pip install -r requirements.txt
                    pytest -v
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t python-api .'
            }
        }

        stage('Run with Docker Compose') {
            steps {
                bat 'docker-compose up -d'
            }
        }
    }
}
