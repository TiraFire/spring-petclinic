pipeline {
  agent any
  environment {
     increase = false
     testpassed = true
  }
  stages {
    stage('Parent') {
        when {
          expression {
            env.increase == false
          }
        }
        stages {
          stage('Build') {
            steps {
              echo env.CommitCount
              echo env.BuildHash
              echo GIT_COMMIT
              //bat './mvnw package'
            
            }
          }
          stage('Test') {
            steps {
              /*try{
                bat "mvn clean test"
              }catch (Exception e){
                 testpassed = false
              }*/
              echo env.testpassed
            }
          }
          stage('Package') {
            when {
              expression {
                env.testpassed == true
              }
            }
            steps {
              echo 'Package'
            }
          }
        }
    }
  }
}
