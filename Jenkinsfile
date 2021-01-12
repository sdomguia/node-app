pipeline {
    agent any
    environment{
        DOCKER_TAG = getDockerTag()

    }
    stages {
        stage( 'build docker Image'){
            steps{
                sh "docker build . -t sdomguia/node-app:${DOCKER_TAG}"
            }
        }
        stage('DockerHub Push'){
            steps{
      withCredentials([string(credentialsId: 'docker-hub', variable: 'dockerHubPwd')]) {
      sh "docker login -u sdomguia -p ${dockerHubPwd}"
      sh "docker push sdomguia/node-app:${DOCKER_TAG}"
}  
        }
    }
}

def getDockerTag(){
    def tag = sh script: 'git rev-parse HEAD', returnStdout: true
    return tag 
}