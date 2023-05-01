pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '$CONNECT "docker build -t my-flask-app ."'}
        }
        stage('Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'my-docker-hub-creds', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                    sh '$CONNET "docker login -u $giantlife -p $BF4qv@Gw$pmJJEa"'
                }
                sh '$CONNET "docker tag my-flask-app giantlife/my-flask-app"'
                sh '$CONNET "docker push giantlife/my-flask-app"'
            }
        }
    }
}
#my name 