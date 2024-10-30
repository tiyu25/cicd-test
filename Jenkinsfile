pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'dev', url: 'https://github.com/tiyu25/cicd-test.git'
            }
        }

        stage('Build and Deploy') {
            steps {
                script {
                    withEnv(['DOCKER_COMPOSE_PATH=/usr/local/bin/docker-compose']) {
                        sh 'docker rm -f jenkins || true'  // 기존 jenkins 컨테이너 강제 중지 및 삭제
                        sh '${DOCKER_COMPOSE_PATH} down'
                        sh '${DOCKER_COMPOSE_PATH} up -d --build'
                    }
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed, check the logs!'
        }
    }
}
