pipeline {
	agent any
	tools {
		maven 'my-maven'
		jdk 'openJDK'
	}
	stages {
		stage('Clone'){
			steps {git url:'https://github.com/DevaNandaRadhakrishnan/SpringSecurity.git', branch:'main'}
		}

		stage('Build'){
			steps {bat "mvn clean install -DskipTests"}
		}
		stage('Test'){
			steps{bat "mvn test"}
		}
		stage('Deploy') {
			steps { bat "docker build -t springsecurity ."
			        bat "docker run -p 8090:8090 -d --name springsecurity springsecurity"}
		}
	}
}

