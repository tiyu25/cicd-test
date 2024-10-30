pipeline {
    agent any
    tools {
        gradle 'gradle'
    }
    stages {
        stage('저장소 복제') {
            steps {
                {복사한 내용}
            }
        }
        stage('빌드') {
            steps {
                sh "./gradlew clean build"
            }
        }
    }
}