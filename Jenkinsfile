pipeline {
  agent any
  stages {
    stage('checkout') {
      steps {
        git(poll: true, url: 'https://github.com/Raman535/cherry', branch: 'master', changelog: true)
      }
    }

    stage('static analysis') {
      steps {
        sh '''echo "Performing static analysis"
pylint *.py
'''
      }
    }

    stage('Code coverage') {
      steps {
        sh 'coverage run -m unittest tests.py'
      }
    }

    stage('Archive') {
      steps {
        archiveArtifacts '*html'
      }
    }

  }
}