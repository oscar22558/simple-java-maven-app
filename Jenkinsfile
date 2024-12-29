pipeline {
    agent any
	tools {
	    maven 'Default' 
	}
	stages {
		stage('Build') { 
		    steps {
				sh 'mvn -B -DskipTests clean package' 
		    }
		}
		stage('Test') {
		    steps {
				sh 'mvn test'
		    }
		    post {
				always {
					junit 'target/surefire-reports/*.xml'
				}
		    }
		}
		stage('Deliver') { 
			steps {
				withCredentials([sshUserPrivateKey(
					credentialsId: 'demo-ssh-key', 
					keyFileVariable: 'prkey', 
					usernameVariable: 'usr'
				)]) {
					sh './jenkins/scripts/deliver.sh' 
				}
			}
		}
	}
}
