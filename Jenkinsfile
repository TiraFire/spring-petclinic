pipeline {
  agent any
  environment {
     increase = false
     testpassed = true
  }
  stages {
    stage('CountIncrease') {
            when {
               env.BuildHash != '' AND env.CommitCount < 8
            }
            steps {
                  echo env.CommitCount
                  echo env.BuildHash
                  echo GIT_COMMIT
                  env.CommitCount = env.CommitCount + 1
                  env.increase = true;
            }
    }
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
