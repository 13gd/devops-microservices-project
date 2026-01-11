pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/13gd/devops-microservices-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-app:latest .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                  docker stop devops-app || true
                  docker rm devops-app || true
                  docker run -d -p 5000:5000 --name devops-app devops-app:latest
                '''
            }
        }
    }
}

