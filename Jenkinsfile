pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stages {
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
        stage('IncreaseCount') {
          steps {
            echo 'Hello'
          }
        }
      }
    }
    

  }
  environment {
    increase = 'true'
    testpassed = 'true'
  }
}
