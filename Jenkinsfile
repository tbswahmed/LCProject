pipeline {
   agent any
   stages {
    stage('Checkout') {
      steps {
        script {
           git branch: 'ahmedtyb', 
           url: 'https://github.com/tbswahmed/LCProject.git'
          }
       }
    }
    stage('Build') {
      steps {
        script {
           sh 'ansible-playbook ansible/build.yml -i ansible/inventory/hosts.yml'
          }
       }
    }
    stage('Docker Build img') {
      steps {
        script {
           sh 'ansible-playbook ansible/docker.yml -i ansible/inventory/hosts.yml'
          }
       }
    }
    stage('pushing to DokcerHub') {
      steps {
        script {
           sh 'ansible-playbook ansible/docker-registry.yml -i ansible/inventory/hosts.yml'
          }
       }
    }
    tage('Monitoring') {
      steps {
        script {
           sh 'ansible-playbook ansible/docker-compose.yml -i ansible/inventory/hosts.yml'
          }
       }
    }
  }
}
