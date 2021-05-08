pipeline {
  agent {
    label 'slave'
  }

  environment {
    vaultCredential ='vaultpass_id'
  }

  stages {
    // clean environment with new files
    stage('Checkout') {
      steps {
        cleanWs()
        checkout scm
      }
    }

    // deploy to staging environment
    stage('Staging deployment') {
      steps {
        ansiblePlaybook credentialsId: '9328c1b9-1174-4afe-9d7c-71b5b6945496', disableHostKeyChecking: true, inventory: 'inventory', playbook: 'deploy.yml', vaultCredentialsId: 'vaultpass_id'
      }
    }

    // approval to deploy to production environment
    stage('Deploy approval') {
      steps {
        input "Deploy to prod?"
      }
    }

    // approval to deploy to production environment
    stage('Deploy approval') {
      steps {
        ansiblePlaybook credentialsId: '9328c1b9-1174-4afe-9d7c-71b5b6945496', disableHostKeyChecking: true, inventory: 'inventory', playbook: 'deploy.yml', vaultCredentialsId: 'vaultpass_id'
      }
    }
  }
  post {
    always {
      deleteDir() /* clean up our workspace */
    }
  }
}