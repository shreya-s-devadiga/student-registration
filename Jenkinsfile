pipeline {
    agent any
    
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/shreya-s-devadiga/student-registration.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t student-registration .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker stop student-registration || true'
                sh 'docker rm student-registration || true'
                sh 'docker run -d -p 8080:80 --name student-registration student-registration'
            }
        }
    }
}
