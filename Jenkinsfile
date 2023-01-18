pipeline {
    agent any // if no Agent then it will bild on jenkins server

	environment {
		MAVEN_HOME = "D:/destros/Maven/maven-3.8.7/"
		JAVA_HOME =  "C:/Program Files/Java/jdk-17/"
	}

    stages {
        stage('Clone-Repo') {
	    steps {
	        checkout scm  // cloning repository
	    }
        }

        stage('Build') {
            steps {
                sh 'mvn install -Dmaven.test.skip=true' // Build the code
            }
        }
		
        stage('Unit Tests') {
            steps {  
                sh 'mvn surefire:test' // running Testcases
            }
        }

        stage('Deployment') {
            steps {
                sh 'sshpass -p "gamut" scp target/gamutgurus.war gamut@172.17.0.3:/home/gamut/Distros/apache-tomcat-9.0.70/webapps'
                sh 'sshpass -p "gamut" ssh gamut@172.17.0.3 "/home/gamut/Distros/apache-tomcat-9.0.70/bin/startup.sh"'
            }
        }
    }
}