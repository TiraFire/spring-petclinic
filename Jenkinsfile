pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
            echo env.BuildHash;  //bat './mvnw package'
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
