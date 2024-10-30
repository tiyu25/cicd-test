pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'dev', url: 'https://github.com/tiyu25/cicd-test.git'
            }
        }
        stage('Build and Deploy') {
            steps {
                script {
                    sh 'docker-compose down'
                    sh 'docker-compose up -d --build'
                }
            }
        }
    }
}
