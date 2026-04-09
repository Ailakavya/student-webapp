pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t student-app .'
            }
        }

        stage('Deploy') {
            steps {
                bat '''
                docker stop student-container || exit 0
                docker rm student-container || exit 0
                docker run -d -p 8081:8080 --name student-container student-app
                '''
            }
        }
    }
}