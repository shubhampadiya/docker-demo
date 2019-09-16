    node {
	    stage('Checkout') {
		checkout scm
				}
		stage('Build Image') {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
				}
		stage('Docker Image Push') {
		    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
			dockerImage.push()
			}
		}
	}
