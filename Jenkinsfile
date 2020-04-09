pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          when {
            expression {
              return env.increase
            }

          }
          steps {
            echo env.CommitCount
            echo env.BuildHash
            echo GIT_COMMIT
          }
        }

        stage('IncreaseCount') {
          steps {
            echo 'Hello'
          }
        }

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
          return env.testpassed
        }

      }
      steps {
        echo env.testpassed+" bye"
      }
    }

  }
  environment {
    increase = 'true'
    testpassed = 'true'
  }
}