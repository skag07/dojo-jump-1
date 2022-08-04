pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('skag07')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t skag07/dojo-jump:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push skag07/dojo-jump:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
