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
		stage ('Deploy to tomcat) {
			steps {
				deploy adapters: [tomcat9(path: '', url: 'http://194.9.172.80:8888/')], contextPath: null, war: '**/*.war'
			}
		}
	}
}
