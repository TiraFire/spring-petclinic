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
				echo "Building"
				script {
                    env.increase = 'true'
				}
			}
		}
		stage('Test') {
			when {
				expression { return env.increase }
			}
			steps {
				script {
					try {
						echo "Testing"//bat 'mvn clean test'
					} catch (e) {
						echo "error"
					}
				}
			}
		}
	}
	post {
		always { 
                        echo BUILD_NUMBER
		}
	}
	environment {
		increase = 'false'
		testpassed = 'true'
		CC = '0'
		Hash = 'none'
	}
}
