pipeline {
    agent any
    environment {
        SSH_CRED = credentials('flask-app-credentials')
        SSH_HOST = 'ec2-3-99-144-68.ca-central-1.compute.amazonaws.com'
        SSH_USER = 'ubuntu'
        IMAGE_NAME = "my-flask-app"
        DOCKERFILE_PATH = "${WORKSPACE}/Dockerfile"
    }
    stages {
        stage('Example') {
            steps {
                script {
                    def CONNECT = sh(script: 'ssh -i ${SSH_CRED} -o StrictHostKeyChecking=no ${SSH_USER}@${SSH_HOST}', returnStdout: true).trim()
                    //def CONNECT=$(ssh -i $(SSH_CRED) -o StrictHostKeyChecking=no ubuntu@ec2-3-99-144-68.ca-central-1.compute.amazonaws.com)
                    //$CONNECT 'docker build -t my-flask-app
                }
            }    
        }
    
        stage('Build') {
            steps {
                sh "docker build -t ${IMAGE_NAME} -f ${DOCKERFILE_PATH} ."
            }
        }
    }
}