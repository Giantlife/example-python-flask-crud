pipeline {
    agent any
    environment {
        SSH_CRED = credentials('flask-app-credentials')
        SSH_HOST = 'ec2-35-183-115-102.ca-central-1.compute.amazonaws.com'
        SSH_USER = 'ubuntu'
        DOCKERHUB_CREDENTIALS = credentials('dockerhub')
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

        stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push giantlife/new-flask-app'
			}
		}
    }

	post {
		always {
			sh 'docker logout'
		}
	}

}