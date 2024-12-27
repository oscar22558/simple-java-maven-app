pipeline {
    agent any
    stages {
	tools {
            maven 'Default' 
	}
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
        }
    }
}
