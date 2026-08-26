pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'YOUR_GITHUB_REPOSITORY_URL'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t nginx-demo .'
            }
        }

        stage('Stop Old Container') {
            steps {
                bat 'docker stop nginx-demo-container || exit 0'
                bat 'docker rm nginx-demo-container || exit 0'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run -d -p 8080:80 --name nginx-demo-container nginx-demo'
            }
        }
    }
}