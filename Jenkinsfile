pipeline {
  agent any
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerHub')
    EXAMPLE_CREDS=credentials(')
    
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t thejika/nodejsapp1:2 .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
       
        sh 'docker push thejika/nodejsapp1:2'
      }
    }
    stage('ssh'){
      steps{
         sh('curl -u $EXAMPLE_CREDS_USR :$EXAMPLE_CREDS_PSW'
        sh 'mkdir /home/ec2-user/test'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
