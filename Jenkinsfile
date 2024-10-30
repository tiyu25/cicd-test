pipeline {
    agent any
    tools {
        gradle 'gradle'
    }
    stages {
        stage('빌드') {
            steps {
                sh "./gradlew clean build"
            }
        }
    }
}