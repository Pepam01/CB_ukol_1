pipeline {
    agent any

    stages {
        stage('check') {
            steps {
                echo 'Check Stage running'
                echo 'Building'
                echo 'Testing'
            }
        }

        stage('release') {
          when {
            expression {
            	env.BRANCH_NAME == 'develop' || env.BRANCH_NAME == 'master'
            }
          }
          // steps pro develop
          steps {
              when {
                  expression {
                      TAG_NAME == 'latest'
                  }
              }
                  steps {
                      echo "Deploying ${ env.BRANCH_NAME }"
                  }

          // steps pro release
              when {
                  expression {
                      TAG_NAME == 'production'
                  }
              }
                  steps {
                      echo "Deploying ${ env.BRANCH_NAME }"
                  }
      }
    }
  }
}
