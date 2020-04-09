pipeline {
	agent any
	stages {
		stage('BuildOrNotToBuild') {
			when {
				anyOf {
					environment name: 'Hash', value: 'none'
					expression { env.CC >= 0 }
				}
				branch 'master'
			}
			steps {
				env.increase = true
				echo "Building"
			}
		}
		stage('Test') {
			when {
				expression { return env.increase }
			}
			steps {
				script {
					try {
						bat 'mvn clean test'
					} catch (e) {
						echo "error"
						throw
					}
				}
			}
		}
	}
	post {
		always { echo "whazzza" }
	}
	environment {
		increase = 'false'
		testpassed = 'true'
		CC = '0'
		Hash = 'none'
	}
}
