pipeline {
  agent any
  parameters {
        string(defaultValue: "TEST", description: 'What environment?', name: 'userFlag')
        choice(choices: ['US-EAST-1', 'US-WEST-2'], description: 'What AWS region?', name: 'region')
    }
  stages {
    stage('Build') {
      steps {
        parallel(
          "Build": {
            echo 'starting Build'
            
          },
          "SCM checkout": {
            sleep 5
            git(poll: true, url: 'https://github.com/siemianowskim/jenkins.git', branch: 'master', changelog: true)
            
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
        sh 'cp README.md test.md'
      }
    }
  }
}
