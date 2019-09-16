pipeline {
  environment {
    registry = "shubhampadiya/gs-spring-boot-docker"
    registryCredential = 'docker-hub-credentials'
    dockerImage = ''
  }
  agent any
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('Building image') {
      steps{
        script {
		    def mvnHome = tool 'apache-maven-3.2.1'
		    def dockerImage = sh "sudo ${mvnHome}/bin/mvn package dockerfile:build"
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
  }
}
