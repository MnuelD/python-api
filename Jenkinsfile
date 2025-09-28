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
                    "C:\\Users\\Elon Tavares\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" -m pip install --upgrade pip
                    "C:\\Users\\Elon Tavares\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" -m pip install -r requirements.txt
                    "C:\\Users\\Elon Tavares\\AppData\\Local\\Programs\\Python\\Python313\\Scripts\\pytest.exe" -v
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
