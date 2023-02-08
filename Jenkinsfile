pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    environment {
    DOCKERHUB_CREDENTIALS = credentials('74734589924')
  }
    stages {

        stage('Build') {
            steps {
                script{
                 app = docker.build("74734589924/my-react-app")
                }
            }
        }
        stage('Test'){
            steps {
                 echo 'Empty'
            }
        }

        stage('Deploy') {
            steps {
                script{
                    docker.withRegistry('https://registry.hub.docker.com', '74734589924') {
                    app.push("${env.GIT_COMMIT}")
                    app.push("latest")
                    }
                }
            }
        }
    }
}