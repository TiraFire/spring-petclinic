pipeline {
  agent any
  stages {
		stage('One') {
			when {
				expression { env.Hash == 'none' || env.CC >= 8 }
				}
			steps {
				echo "hello"
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
