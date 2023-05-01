pipeline {
    agent any
    environment {
        SSH_CRED = credentials('flask-app-credentials') 
        def CONNECT = "ssh -o StrictHostKeyChecking=no ubuntu@ec2-35-183-10-217.ca-central-1.compute.amazonaws.com"
    }
    stages {
        stage('Build') {
            steps {
                sh "$CONNECT 'docker build -t my-flask-app .'"
            }
        }
        stage('Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'my-docker-hub-creds', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                    sh "$CONNECT 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'"
                }
                sh "$CONNECT 'docker tag my-flask-app giantlife/my-flask-app'"
                sh "$CONNECT 'docker push giantlife/my-flask-app'"
            }
        }
    }
}
