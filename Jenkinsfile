pipeline {
    agent any

    environment {
        REPO_URL = 'https://github.com/Bhargavi-6519/Docker.git'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: "$REPO_URL", branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'npm install'
                    sh 'docker build -t my-docker-image .'
                }
            }
        }

        stage('Deploy Docker Container') {
            steps {
                script {
                    sh 'docker run -d -p 80:80 my-docker-image'
                }
            }
        }
    }

    post {
        success {
            echo "Build and Deployment were successful!"
        }
        failure {
            echo "Build or Deployment failed!"
        }
    }
}
