pipeline {
  agent any
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerHub')
    EXAMPLE_CREDS=credentials('44.211.198.19')
    
  }
 // stages {
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
        echo ===>about to ssh
        sh '''#!/bin/bash
        ssh -tt linux@44.211.198.19
        ls'''
        
       
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
