pipeline {
  agent any

  stages {
    stage('Checkout (job SCM)') {
      steps {
        // Uses the repository & branch configured in the Jenkins job itself
        checkout scm
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t student-registration:${BUILD_NUMBER} .'
      }
    }

    stage('Run Docker Container') {
      steps {
        sh 'docker stop student-registration || true'
        sh 'docker rm student-registration || true'
        sh "docker run -d -p 8080:80 --name student-registration -e BUILD_NUMBER=${BUILD_NUMBER} student-registration:${BUILD_NUMBER}"
      }
    }
  }
}
