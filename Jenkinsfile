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
    }
}

def getdockerTag(){
    def tag = sh script: 'git rev-parse HEAD', returnStdout: true
    return tag 
}