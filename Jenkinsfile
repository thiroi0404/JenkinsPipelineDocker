pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-nginx-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                    docker stop my-nginx || true
                    docker rm my-nginx || true
                '''
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d --name my-nginx -p 80:80 my-nginx-app'
            }
        }

        stage('Check') {
            steps {
                sh 'docker ps'
            }
        }
    }
}