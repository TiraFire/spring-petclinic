pipeline {
	agent any
	stages {
		stage('One') {
			when {
				anyOf {
					environment name: 'Hash', value: 'none'
					expression { env.CC >= 0 }
				}
			}
			steps {
				echo "attempt1
			}
		}
	}
	post {
		always { echo "whazzza" }
	}
	environment {
		increase = 'true'
		testpassed = 'true'
		CC = '0'
		Hash = 'none'
	}
}
