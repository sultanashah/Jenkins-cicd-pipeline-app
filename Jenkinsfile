pipeline {
    agent any

    environment {
        IMAGE_NAME = 'jenkins-demo-app'
        PORT = '3000'
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/sultanashah/Jenkins-cicd-demo-app.git'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Test') {
            steps {
                echo 'No tests added yet!'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker run -d -p $PORT:3000 --name demo-app $IMAGE_NAME'
            }
        }
    }

    post {
        always {
            echo 'Pipeline complete.'
        }
    }
}
