pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t nginx-demo .'
            }
        }

        stage('Stop Old Container') {
            steps {
                bat 'docker stop nginx-demo-container || exit /b 0'
                bat 'docker rm nginx-demo-container || exit /b 0'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run -d -p 8081:80 --name nginx-demo-container nginx-demo'
            }
        }
    }
}
