pipeline {
  agent {
    docker {
      image 'node:lts-bullseye-slim'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('build') {
      steps {
        sh 'npm install'
      }
    }

    stage('Test') {
      environment {
        CI = 'true'
      }
      steps {
        sh '''npm test
'''
      }
    }

    stage('Deliver') {
      steps {
        sh 'npm start'
        input '"Proceed" to continue'
        sh './jenkins/scripts/kill.sh.'
      }
    }

  }
}