pipeline {
    agent any

    stages {
// check stage probehnou vsechny branche
        stage('check') {
            steps {
                echo 'Check Stage running'
                echo 'Building'
                echo 'Testing'
            }
        }


// tuhle stage probehnou jen develop a master
// todo rozdelit jeste develop a master, podle ceho ale
        stage('release') {
          when {
            expression {
            	env.BRANCH_NAME == 'develop' || env.BRANCH_NAME == 'master'
            }
          }
          steps {
          // steps pro develop
            when { TAG_NAME == 'latest' }
                  steps {
                      echo "Deploying ${ env.BRANCH_NAME }"
                  }

          // steps pro release
            when { TAG_NAME == 'production' }
                  steps {
                      echo "Deploying ${ env.BRANCH_NAME}"
                  }
      }
    }
  }
}
