//TODO
// skripty nejsou napsane, nevim co maji delat, ale u buildu to bude asi nejaky Gradle job
// a push_Docker_img bude asi pouziti toho pluginu CB kde Gradle copy/pastuje to co zbuildoval a Docker z toho dela Docker img??

//NOTES
// na me Jenkins tato pipeline pada, jeden z duvodu je podle me ten globalni tag ktery ja nemam v Jenkins naklikany.

pipeline {
    agent any
    environment {
        RELEASE_VERSION = 'none'       // definuju jako lokalni promennou, je jmeno tagu v CB Jenkins RELEASE_VERSION?
    }
    stages {
        stage('check') {
            steps {
                sh './scripts/build.sh' // Gradle build?
                sh './scripts/test.sh'
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
                      env.RELEASE_VERSION = 'latest'
                  }

          // steps pro master branch
              when {
                  expression {
                      env.BRANCH_NAME == 'master'
                  }
              }
                  steps {
                      echo "Setting RELEASE_VERSION tag to production"
                      env.RELEASE_VERSION = 'production'
                  }
              sh './scripts/push_Docker_img.sh'
      }
    }
  }
}
