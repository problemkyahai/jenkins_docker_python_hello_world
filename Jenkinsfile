pipeline {
	agent any
	
	environment {
		DOCKER_IMAGE = 'hello-world-python:latest' // Docker image name
	}
	
	stages {
		stage('Checkout') {
			steps {
				git branch: 'main', url: 'https://github.com/problemkyahai/jenkins_docker_python_hello_world.git'
			}
		}
		
		stage('Docker Build') {
			steps {
				script {
					if (fileExists('Dockerfile')) {
						sh "docker build -t ${env.DOCKER_IMAGE} ."
					} else {
						error "Dockerfile not found."
					}
				}
			}
		}
		
		stage('Docker Run') {
			steps {
				sh "docker run --rm ${env.DOCKER_IMAGE}"
			}
		}
	}
	
	post {
		success {
			echo 'Success.'
		}
		failure {
			echo 'Docker build or run failed/'
		}
	}
}
