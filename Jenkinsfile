pipeline {
	agent any

	stages {
	    stage('Checkout') {
	        steps {
				checkout scm
			}
		}
		stage('Build') {
	        steps {
				sh '/home/raja/devops/apache-maven-3.6.1/bin/mvn install'
	        }
		}
		stage('Deployment') {
			steps {
				sh 'sshpass -p "1234" scp target/gamutkart.war raja@172.17.0.2:/home/raja/Devops/apache-tomcat-9.0.16/webapps'
				sh 'sshpass -p "1234" ssh raja@172.17.0.2 "JAVA_HOME=/home/raja/Devops/jdk1.8.0_201" "/home/raja/Devops/apache-tomcat-9.0.16/bin/./startup.sh"'
			}
		}

	}
}
