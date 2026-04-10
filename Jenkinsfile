pipeline{
	
	environment{
		DOCKER_IMAGE='hello-world-python:latest'
	}

	stages{
		stage('Checkout'){
			steps{
				git branch: 'main', url:' https://github.com/s-god-rimuru/jenkins-demo-2.git '
			}
		}
		stage('Docker Bulid'){
			step{
				script{
					if (fileExist('Dockerfile)){
						sh 'docker build -t ${env.DOCKER_IMAGE} .'
					}else{
						error "Dockerfile not found in the workspace"	
					}
				}
			}
		}
	
		stage('Docker Run'){
			step{
				sh "docker run --rm ${$env.DOCKER_IMAGE}"
			}
		}
	}
	
	post{
		success{
			echo'Success'
		}
		
		failure{
			echo 'Failure'
		}
	}
}
