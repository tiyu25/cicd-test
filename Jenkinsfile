pipeline {
    agent any

    environment {
        IMAGE_NAME = "your-docker-image"       // Docker Hub에 푸시할 이미지 이름
        DOCKER_CREDENTIALS_ID = 'docker-hub'   // Jenkins에 등록한 Docker Hub 인증 정보 ID
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                sh './mvnw clean package' // Maven 빌드 예시 (Gradle 사용 시 변경)
            }
        }

        stage('Docker Build & Push') {
            steps {
                script {
                    echo 'Building Docker Image...'
                    sh "docker build -t $IMAGE_NAME ."

                    echo 'Logging in to Docker Hub...'
                    withCredentials([usernamePassword(credentialsId: "$DOCKER_CREDENTIALS_ID", usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                        sh "echo $PASSWORD | docker login -u $USERNAME --password-stdin"
                    }

                    echo 'Pushing Docker Image...'
                    sh "docker push $IMAGE_NAME"
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying...'
                sh "docker run -d -p 8080:8080 $IMAGE_NAME"
            }
        }
    }
}
