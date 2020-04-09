pipeline {
  agent any
  stages {
    stage('Build') {
      when {
        expression {
          env.BuildHash = '' OR env.CommitCount >= 8
        }
      }
      steps {
        echo env.CommitCount
        echo env.BuildHash
      }
    }

    stage('Test') {
      steps {
        echo 'Testing'
      }
    }

    stage('Package') {
      steps {
        echo 'Package'
      }
    }

    stage('Deploy') {
      when {
        expression {
          GIT_BRANCH != 'master'
        }
      }
      steps {
        echo 'Deploy'
      }
    }

  }
}
