pipeline {
  agent {
    node {
      label 'slave'
    }

  }
  stages {
    stage('Echo') {
      steps {
        sh 'echo \'Bla\''
        sh 'python -V'
      }
    }
    stage('Git checkout') {
      steps {
        git(url: 'https://github.com/svarogrud/training-ci', branch: 'master', credentialsId: '424e300d-c68d-4ce5-acb1-7016dc9a489a')
      }
    }
    stage('Run app') {
      steps {
        dir(path: 'flask-app') {
          sh 'docker-compose up -d --build'
        }

      }
    }
    stage('Run Tests') {
      steps {
        dir(path: 'flask-app') {
          sh '''docker-compose down
docker-compose build flask-app
docker-compose run flask-app pytest -v --junit-xml=/var/opt/junit-report/report.xml
docker-compose down'''
        }

      }
    }
  }
}