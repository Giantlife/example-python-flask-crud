pipeline {
    agent any
    environment {
        SSH_CRED = credentials('flask-app-credentials')
        SSH_HOST = 'ec2-3-98-58-81.ca-central-1.compute.amazonaws.com'
        SSH_USER = 'ubuntu'
        
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
                sh 'docker build -t giantlife/new-flask-app -f /home/ubuntu/example-python-flask-crud/Dockerfile .'
            }
        }
    }
}
        stage('Login') {

			steps {
				  withCredentials([usernamePassword(credentialsId: 'jenkins-app-deploy', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                    sh "docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD"
			}
		}
        }