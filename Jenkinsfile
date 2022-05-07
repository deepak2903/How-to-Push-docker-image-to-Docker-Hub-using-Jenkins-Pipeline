pipeline{

	/* agent {label 'linux'} */
	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub_id')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git 'https://github.com/deepak2903/How-to-Push-docker-image-to-Docker-Hub-using-Jenkins-Pipeline.git'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t deepak2903/nodeapp_test:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push thetips4you/nodeapp_test:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
