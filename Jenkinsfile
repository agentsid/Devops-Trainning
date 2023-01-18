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
				print "Deployment is done!"
				sh ' scp target/gamutkart.war siddharth@192.168.1.75:/home/siddharth'
                //sh 'cp C:/Users/Admin/.jenkins/workspace/pipeline/target/gamutkart.war C:/Program Files/Apache Software Foundation/Tomcat 10.0/webapps/'
                
            }
        }
    }
}