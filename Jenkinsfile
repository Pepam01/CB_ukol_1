pipeline {
    agent any
    //environment {
    //    RELEASE_VERSION = 'none'       // definuju jako lokalni promennou, je jmeno tagu v CB Jenkins RELEASE_VERSION?
    //}
    stages {
        stage('check') {
            steps {
                echo "Check Stage of branch ${env.BRANCH_NAME} running..."
            }
        }

        stage('release') {
          when {
            expression {
            	env.BRANCH_NAME == 'develop' || env.BRANCH_NAME == 'master'
            }
          }
          // steps pro develop branch
          steps {
              when {
                  expression {
                      env.BRANCH_NAME == 'develop'
                  }
              }
                  steps {
                      echo "Setting RELEASE_VERSION tag to latest"
                      //env.RELEASE_VERSION = 'latest'
                  }

          // steps pro master branch
              when {
                  expression {
                      env.BRANCH_NAME == 'master'
                  }
              }
                  steps {
                      echo "Setting RELEASE_VERSION tag to production"
                      //env.RELEASE_VERSION = 'production'
                  }
      }
    }
  }
}
