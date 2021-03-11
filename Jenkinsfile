pipeline {
	agent any
	
	stages {
		stage ('Build') {
			steps {
				git 'https://github.com/JosueVass/app.git'
			    
			    bat 'mvn clean'
				bat 'mvn -B compile'
			}
		}
		stage ('Test') {
			steps {
				bat 'mvn test'
			}
			post {
				success {
				    echo "Terminó exitosamente"
				}
				failure {
				    echo "Terminó con error"
				}
				always {
				    junit 'target/surefire-reports/*.xml'
				}
			}
		}
		stage ('Package') {
			steps {
			    echo "Se ha empaguetado la aplicación"
				bat 'mvn package'
			
				archiveArtifacts 'target/*.jar'
			}
		}
	}
}
