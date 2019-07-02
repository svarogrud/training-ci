pipeline {
  agent {
    node {
      label 'master'
    }

  }
  stages {
    stage('Echo') {
      steps {
        sh 'echo \'Bla\''
      }
    }
    stage('Git checkout') {
      steps {
        git(url: 'https://github.com/svarogrud/training-ci', branch: 'master', credentialsId: '424e300d-c68d-4ce5-acb1-7016dc9a489a')
      }
    }
  }
}