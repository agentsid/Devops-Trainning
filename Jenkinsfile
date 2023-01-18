pipeline {
    agent any

	tools {
		maven 'maven3.8.7'
		java 'java17'
	}

	environment {
		MAVEN_HOME = "D:/destros/Maven/maven-3.8.7/bin"
		JAVA_HOME = "C:/Program Files/Java/jdk-17/bin"
	}

    stages {
		stage('Clone-Repo') {
			steps {
				checkout scm
			}
		}
		stage('Build') {
	    	steps {
				sh 'mvn install -DskipTests'
			}
	    }
		stage('Unit Tests') {
			steps {
				sh 'mvn surefire:test'
			}
		}
		stage('Deployment') {
	    	steps {
				print "Deployment is done!"
//				sh 'sshpass -p "gamut" scp target/gamutkart.war gamut@172.17.0.3:/home/gamut/Distros/apache-tomcat-8.5.41/webapps'
//				sh 'sshpass -p "gamut" ssh gamut@172.17.0.3 "JAVA_HOME=/home/gamut/Distros/jdk1.8.0_211" "/home/gamut/Distros/apache-tomcat-8.5.41/bin/startup.sh"'
	    	}
		}
    }
}
