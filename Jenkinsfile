pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('tcampest-dockerhub')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t tcampest/nodeapp:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push tcampest/nodeapp:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}

