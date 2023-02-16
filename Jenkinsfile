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
// todo rozdelit jeste develop a master
        stage('release') {
          when { branch 'develop' || branch 'master' }
            steps {
                echo 'Release stage running'
                echo 'Deploying master or develop'
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
