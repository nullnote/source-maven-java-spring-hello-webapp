pipeline {
	agent {
	  label "jenkins-node"
	}
	triggers {
	  pollSCM('* * * * *')
	}
	
	stages {
		stage('Checkout') {
			steps {
				git branch: 'main',
				url: 'https://github.com/nullnote/source-maven-java-spring-hello-webapp'
			}
		}
		stage('Build') {
			steps {
				sh 'mvn clean package'
			}
		}
		stage('Test') {
			steps {
				sh 'mvn test'
			}
		}
		stage('Deploy') {
			steps {
				deploy adapters: [tomcat9(credentialsID: 'tomcat-manager', url: 'http://192.168.56.102:8080'], contextPath: null, war: 'path/to/war'
			}
		}
	}
}
