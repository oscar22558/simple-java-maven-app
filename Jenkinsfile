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
    }
}
