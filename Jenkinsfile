pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo env.CommitCount
        echo env.BuildHash
        echo GIT_COMMIT
      }
    }

    stage('Test') {
      steps {
        echo env.testpassed
      }
    }

    stage('Package') {
      when {
        expression {
          env.testpassed == 'true'
        }

      }
      steps {
        echo 'Package'
      }
    }

  }
  environment {
    increase = 'false'
    testpassed = 'true'
  }
}
