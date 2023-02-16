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
                echo "Deploying ${ env.BRANCH_NAME }"
            }
        }
    }
}


// takhle pres env promenne, ja to ale delam pres property? Nevim jak se tomu rika
//if (env.BRANCH_NAME == "deployment") {
//    ... do some build ...
//} else {
//    ... do something else ...
//}
