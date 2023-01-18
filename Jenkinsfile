pipeline {
    agent any

	// tools {
	// 	jdk 'jdk17'
	// }
	environment {
		MAVEN_HOME = "D:/destros/Maven/maven-3.8.7/bin"
		JAVA_HOME =  "C:/Program Files/Java/jdk-17/bin"
	}

    stages {
        stage('Clone-Repo') {
	    steps {
	        checkout scm
	    }
        }

        stage('Build') {
            steps {
                sh 'mvn install -Dmaven.test.skip=true'
            }
        }
		
        stage('Unit Tests') {
            steps {
                //sh 'mvn compiler:testCompile'
                sh 'mvn surefire:test'
                //junit 'target/**/*.xml'
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