pipeline {
	agent any
	tools{
		maven 'Maven'
	}
	stages{
		stage('checkout'){
			steps{
				git branch:'master',url:'https://github.com/SameekshaPrabha06/mvnans.git'
			}
		}
		stage('build'){
			steps{
				sh 'mvn clean package'
			}
		}
		stage('archive'){
			steps{
				archiveArtifacts artifacts: 'target/*.war',fingerprint:true
			}
		}
		stage('deploy'){
			steps{
				sh 'ansible-playbook ansible/playbook.yml -i hosts.ini'
			}
		}
	}
}
