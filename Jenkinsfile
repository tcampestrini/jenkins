pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('bernardo9999')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t bharathirajatut/nodeapp:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo 21054ffb-417a-42fc-9cf0-f195cc95c440 | docker login -u bernardo9999 --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push jenkins-example/nodeapp:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
