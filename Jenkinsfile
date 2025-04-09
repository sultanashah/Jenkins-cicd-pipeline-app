pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t jenkins-demo-app .'
            }
        }

        stage('Test') {
            steps {
                echo '🧪 Skipping actual tests for now...'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker stop demo-app || true'
                sh 'docker rm demo-app || true'
                sh 'docker run -d --name demo-app -p 3000:3000 jenkins-demo-app'
            }
        }
    }
}
