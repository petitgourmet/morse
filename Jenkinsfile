pipeline {
  agent any
  environment {
    HOME = "${env.WORKSPACE}"
  }
  stages {
    stage('build') {
      steps {
        sh 'pip install pipenv --user'
        sh '~/.local/bin/pipenv install --dev'
      }
    }
    stage('test') {
        steps {
          sh '~/.local/bin/pipenv run nosetests'
        }
    }
  }
}
