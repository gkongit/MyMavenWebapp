pipeline {
	agent any
	
	tools {
		maven 'Maven'
	}
	
	stages {
		stage('Checkout') {
			steps {
				git branch: 'main', url: 'https://github.com/gkongit/MyMavenWebapp.git'
			}
		}
		
		stage('Build') {
			steps {
				sh 'mvn clean install'
			}
		}
		
		stage('Archive') {
			steps {
				archiveArtifacts artifacts: 'target/*.war', fingerprints: true 
			}
		}
		
		stage('Deploy') {
			steps {
				sh 'ansible-playbook ansible/playbook.yml -i ansible/hosts.ini'
			}
		}
	}
}
