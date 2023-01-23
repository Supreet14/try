pipeline {
  agent any
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerHub')
  }
  stages {
    /*stage('Build') {
      steps {
        sh 'docker build -t supreet14/nodejsapp:2 .'
      }
    }*/
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    /*stage('Push') {
      steps {
        sh 'docker push supreet14/nodejsapp:2'
      }
    }
  }*/
   stage('EC2')
    {
      steps{
        sshagent(['44.211.198.19'])
        {
          sh'''ssh -o StrictHostKeyChecking=no -l ec2-user 3.86.83.128 uname -a
               git --version'''
        }
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
