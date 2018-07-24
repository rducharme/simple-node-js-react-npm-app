pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh 'npm install'
      }
    }
    stage('Test') {
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }
    stage('Deliver') {
      steps {
        sh './jenkins/scripts/deliver.sh'
        input(message: 'Finished using the web site?', id: 'Proceed')
        sh './jenkins/scripts/kill.sh'
      }
    }
  }
  environment {
    CI = 'true'
  }
}