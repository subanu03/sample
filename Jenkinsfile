pipeline {
    agent any

    stages {

        stage('Clone GitHub Repo') {
            steps {
                git 'https://github.com/subanu03/python-jenkins-docker.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t python-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker stop python-container || true
                docker rm python-container || true
                '''
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run -d --name python-container -p 5000:5000 python-app'
            }
        }
    }
}
