pipeline {
  agent any
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerHub')
    SSH_CREDS=credentials('44.211.198.19')
    
  }
 stages {
  //  stage('Build') {
    //  steps {
      // sh 'docker build -t thejika/nodejsapp1:2 .'
    // }
  //  }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
   // stage('Push') {
    // steps {
       
      // sh 'docker push thejika/nodejsapp1:2'
     // }
  //  }
    stage('ssh'){
      steps{
        sh 'echo "ssh private $SSH_CREDS"'
       // sh 'curl -u $EXAMPLE_CREDS_USR:$EXAMPLE_CREDS_PSW '
        sh '''#!/bin/bash
        ssh -tt ec2-user@44.211.198.19
       
        '''
        
       
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
