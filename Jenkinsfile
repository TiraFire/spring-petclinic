pipeline {
  agent any
  stages {
    stage('CountIncrease') {
            when {
              expression { env.BuildHash != '' && env.CommitCount < 8 }
            }
            steps {
                  echo env.CommitCount
                  echo env.BuildHash
                  echo GIT_COMMIT
                  env.CommitCount = env.CommitCount + 1
                  env.increase = false;
            }
    }
    stage('Build') {
      when {
        expression { return env.increase }
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
  environment {
    increase = 'true'
    testpassed = 'true'
  }
}
