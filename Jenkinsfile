pipeline {
  agent any
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerHub')
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t thejika/nodejsapp:1 .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push thejika/nodejsapp:1'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}