pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building..'
        sh 'sudo yum update -y'
      }
    }
    stage('Test') {
      steps {
        echo 'Testing..'
        input(message: 'approved', id: 'aprove', ok: 'ok')
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying....'
      }
    }
  }
}