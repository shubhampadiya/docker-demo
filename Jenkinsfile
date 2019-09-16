  node {
	    stage('Checkout') {
		checkout scm
				}
		stage('Build Image') {
		    def mvnHome = tool 'apache-maven-3.2.1'
		    def dockerImage = sh "sudo ${mvnHome}/bin/mvn package dockerfile:build"
				}
		stage('Docker Image Push') {
		    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
			dockerImage.push()
			}
		}
	}
