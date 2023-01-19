pipeline {
  agent any
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerHub')
   // SSH_CREDS=credentials('44.211.198.19')
    
  }
 stages {
  //  stage('Build') {
    //  steps {
      // sh 'docker build -t thejika/nodejsapp1:2 .'
    // }
  //  }
   // stage('Login') {
    //  steps {
     //   sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
     // }
   // }
   // stage('Push') {
    // steps {
       
      // sh 'docker push thejika/nodejsapp1:2'
     // }
  //  }
    stage('ssh'){
     // environment {
      //  SSH_CREDS = credentials('44.211.198.19')
     // }
      steps{
        sh 'echo "SSH private is loacted at $SSH_CREDS"'
       // sh 'echo "SSH user is $SSH_CREDS_USR"'
        sh 'ssh -t $SSH_CREDS ec2-user@3.82.212.252'
         sh 'chmod 400 $SSH_CREDS'
       sh 'ssh -tt ec2-user@$SSH_CREDS@3.82.212.252'
   
        sh 'curl -u $SSH_CREDS_USR:$SSH_CREDS_PSW '
        sh '''#!/bin/bash
          'pwd'
       
       '''
       // withCredentials([sshUserPrivateKey(credentialsId: '44.211.198.19',keyFileVariable:'password')])
       // sh 'ssh -t ${password} ec2-user@3.82.212.252'
        //sh 'chmod 400 ${password}'
       // sh 'ssh -tt ${password} ec2-user@3.82.212.252'
       // sh 'pwd'
      }
      stage('connect to ssh') {
      steps {
        sh 'mkdir /home/ec2-user/test'
      }
    }
  }
 // post {
   // always {
     // sh 'docker logout'
  //  }
 // }
}
