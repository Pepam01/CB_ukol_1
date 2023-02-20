pipeline {
  agent any
  stages {
    stage('check') {
      steps {
        sh './scripts/build.sh' // Gradle build?
        sh './scripts/test.sh'
        echo "Check Stage of branch ${env.BRANCH_NAME} running..."
      }
    }

    stage('release') {
    environment {
    	RELEASE_VERSION = 'none'
    	ENVIRONMENT_TAG = getEnvTag(env.BRANCH_NAME)
    }
      when {
        expression {
          env.BRANCH_NAME == 'develop' || env.BRANCH_NAME == 'master'
        }
      }
      // steps pro develop branch
      steps {
	echo "ENV_tag value :  ${ENVIRONMENT_TAG}"
	sh "chmod +x -R ${env.WORKSPACE}"
        sh './scripts/push_Docker_img.sh'
      }
    }
  }
}

def getEnvName(branchName) {
    if("master".equals(branchName)) {
        return "production";
    } else if("production".equals(branchName)) {
        return "latest";
    }
}
