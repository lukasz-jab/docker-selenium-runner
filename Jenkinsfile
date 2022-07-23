pipeline {
	agent any
	stages {
		stage("Run Grid") {
			steps {
				bat "docker-compose up -d --no-color hub chrome firefox"
			}
		}
		stage("Run Tests") {
			steps {
				bat "docker-compose up --no-color tour duck"
			}
		}
	}
	post {
		always {
			archiveArtifacts artifacts: 'tests-out\\**'
			bat "docker-compose down"
		}
	}
}