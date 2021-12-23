pipeline {
    agent any
	tools {
	    maven "maven-3.8.4"
	 	}
	stages {
	    stage('Git CheckOut') {
		    steps {
			   checkout([$class: 'GitSCM', branches: [[name: '*/dragon']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/logicopslab/rock-paper-scissors.git']]])
			}
		}
        stage('Clean and Install') {
            steps {
                bat 'mvn clean install'
            }
        }
        stage ('Code Quality'){
            steps {
                    withSonarQubeEnv('SonarQubeServer') {
                bat 'mvn sonar:sonar'
                }
             }
        }
		
    }
}
