pipeline {
    agent any
    environment {
        SSH_CRED = credentials('flask-app-credentials')
        SSH_HOST = 'ec2-3-98-58-81.ca-central-1.compute.amazonaws.com'
        SSH_USER = 'ubuntu'
        DOCk = credentials('my-docker-hub-creds')
    }
    stages {
        stage('Example') {
            steps {
                script {
                    def CONNECT = sh(script: 'ssh -i ${SSH_CRED} -o StrictHostKeyChecking=no ${SSH_USER}@${SSH_HOST}', returnStdout: true).trim()
                    //$CONNECT 'docker build -t new-flask-app
                }
            }    
        }
    
        stage('Build') {
            steps {
                sh 'docker build -t giantlife/new-flask-app .'
            }
        }
    }
}
        stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}