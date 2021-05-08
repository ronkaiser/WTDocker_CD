pipeline {
  agent {
    label 'slave'
  }

  environment {
    dockerImage =''
    registry = 'ronkaiser86/wtapp:$BUILD_NUMBER'
    registryCredential ='dockerhub_id'
  }

  // clean environment with new files
  stages {
    stage('Checkout') {
      steps {
        cleanWs()
        checkout scm
      }
    }
  }
}