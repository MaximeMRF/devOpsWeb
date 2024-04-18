pipeline{
	agent any
	tools {
		maven 'local_maven'
	}
	stages{
		stage ('Build') {
			steps {
				sh 'mvn clean package'
			}
			post{
				success {
					echo 'Archiving the artifacts'
					archiveArtifacts artifacts: '**/target/*.war'
				}
			}	
		}
		stage ('Deploy to tomcat') {
			steps {
				deploy adapters: [tomcat7(credentialsId: '1d314e7e-70df-43df-824e-87fb0ff3e138', path: '', url: '')], contextPath: null, war: '**/*.war'
			}
		}
	}
}
