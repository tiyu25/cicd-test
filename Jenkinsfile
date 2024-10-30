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
                    withEnv(['DOCKER_COMPOSE_PATH=/usr/local/bin/docker-compose']) {
                        sh '$DOCKER_COMPOSE_PATH down'
                        sh '$DOCKER_COMPOSE_PATH up -d --build'
                    }
                }
            }
        }
    }
}
