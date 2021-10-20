pipeline {
  // https://hub.docker.com/repository/docker/takinosaji/msdp-cicd-practice/general
  agent any
  environment {
      DOCKER_ACCESS_TOKEN = credentials('docker-hub-access-token')
  }
  // There is no need to add additional SCM Checkout step. Entire repository has been checked out with pipeline
  stages {
    stage('Application build') {
      steps {
        sh 'chmod +x scripts/build.sh'
        sh 'sh scripts/build.sh'
      }
    }

    stage('Run tests') {
      steps {
        sh 'scripts/test.sh'
      }
    }

    stage('Docker image build') {
      steps {
        sh 'docker build -t takinosaji/msdp-cicd-practice:$BUILD_NUMBER -t takinosaji/msdp-cicd-practice:latest .'
      }
    }

    stage('Docker image push') {
      steps {
        sh 'docker login -u takinosaji -p $DOCKER_ACCESS_TOKEN'
        sh 'docker push takinosaji/msdp-cicd-practice:$BUILD_NUMBER'
        sh 'docker push takinosaji/msdp-cicd-practice:latest'
      }
    }
  }
}