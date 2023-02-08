pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  environment {
    DOCKERHUB_CREDENTIALS = credentials('74734589924')
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t 74734589924/my-react-app:${env.BUILD_ID} .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push 74734589924/my-react-app:${env.BUILD_ID}'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}