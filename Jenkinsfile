pipeline {
  agent {
    label 'slave'
  }

  environment {
    vaultCredential ='vaultpass_id'
  }

  // clean environment with new files
  stages {
    stage('Checkout') {
      steps {
        cleanWs()
        checkout scm
      }
    }
    stage('Staging deployment') {
      steps {
        ansiblePlaybook credentialsId: '9328c1b9-1174-4afe-9d7c-71b5b6945496', disableHostKeyChecking: true, inventory: 'inventory', playbook: 'deploy.yml', vaultCredentialsId: 'vaultpass_id'
      }
    }
  }
}