pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t python-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                bat 'docker stop python-app || exit 0'
                bat 'docker rm python-app || exit 0'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat 'docker run -d -p 5000:5000 --name python-app python-app'
            }
        }
    }
}


