pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        parallel(
          "Build": {
            echo 'starting Build'
            
          },
          "SCM checkout": {
            sleep 5
            
          },
          "Lunch Ansible": {
            sleep 5
            
          }
        )
      }
    }
    stage('Test') {
      steps {
        echo 'Verfiy build'
        input(message: 'Want to deploy into DEV?', id: 'aprove', ok: 'ok')
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying....'
        sh '''sudo yum install htop -y && sudo cp /var/log/messages /tmp/
'''
      }
    }
  }
}