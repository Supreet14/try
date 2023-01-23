pipeline {
  agent any
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerHub')
  }
  stages {
    /*stage('Build') {
      steps {
        sh 'docker build -t thejika/thejika:1 .'
      }
    }*/
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
   /* stage('Push') {
      steps {
        sh 'docker push thejika/thejika:1'
      }
    }*/
  
   stage('Ansible')
    {
      steps{
          ansiblePlaybook credentialsId: 'webserver', disableHostKeyChecking: true, installation: 'ansible', inventory: 'inventory.inv', playbook: 'ansible.yml'
          //sh"""ssh -o StrictHostKeyChecking=yes -l ec2-user 54.250.107.129 uname -a  
               //docker images
          //sh'docker --version'
          //sh'sudo service docker start'
          //sh'docker pull supreet14/nodejsapp:2'
          //sh'docker run supreet14/nodejsapp:2'
          //sh'docker images'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
}
}

     
