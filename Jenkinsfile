any {
    stage('Clone repository') {
        git credentialsId: 'git', url: 'https://github.com/Andrew1988123123/scramjet'
    }

    stage('Build image') {
       dockerImage = docker.build("Andrew1988123123/my-react-app:latest")
    }

 stage('Push image') {
        withDockerRegistry([ credentialsId: "123456", url: "" ]) {
        dockerImage.push()
        }
    }
}