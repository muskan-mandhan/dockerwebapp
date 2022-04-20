pipeline{

	

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git 'https://github.com/muskan-mandhan/jenkins-demo.git'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t 239910/jenkins-docker demo:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push 239910/jenkins-docker demo:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
