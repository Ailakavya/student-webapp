pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t student-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 8081:8080 student-app'
            }
        }
    }
}
=======
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
>>>>>>> c0aed952b646e655f32a0d0573b7fff0bf68b7bd
