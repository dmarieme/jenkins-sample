// Powered by Infostretch 

timestamps {

node () {

	stage ('App-IC - Checkout') {
 	 checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'git-login', url: 'https://github.com/dmarieme/jenkins-sample.git']]]) 
	}
	stage ('App-IC - Clean') {
 	
	withMaven(maven: 'maven') { 
 			if(isUnix()) {
 				sh "mvn clean " 
			} else { 
 				bat "mvn clean " 
			} 
 		}	
	}
	stage ('App-IC - Compile') {
	withMaven(maven: 'maven') { 
 			if(isUnix()) {
 				sh "mvn compile " 
			} else { 
 				bat "mvn compile " 
			} 
 		}	
	}	
	
	stage ('App-IC - Test') {
	 withMaven(maven: 'maven') { 
 			if(isUnix()) {
 				sh "mvn test " 
			} else { 
 				bat "mvn test " 
			} 
 		}	
        }	
		
	stage ('App-IC - Package') {
	withMaven(maven: 'maven') { 
 			if(isUnix()) {
 				sh "mvn package -DskipTests " 
			} else { 
 				bat "mvn package -DskipTests " 
			} 
 		}
	}
	
	stage('Quality check') {
	  withSonarQubeEnv('Sonar') {
	  bat "mvn sonar:sonar"
   }
		
} 

	
}
}
