pipeline {
  agent any
  stages {
    stage('Application build') {
      steps {
        sh 'scripts/build.sh'
      }
    }

    stage('Run tests') {
      steps {
        sh 'scripts/test.sh'
      }
    }

    stage('Prepare image') {
      steps {
        sh 'scripts/test.sh'
      }
    }

  }
}