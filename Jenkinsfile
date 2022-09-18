pipeline{
    agent any
    environment {
      JAVA_VERSION="11"
      DEVOPS_BATCH="AUG2022"
    }
    
    tools {
      jdk 'jdk11'
      maven 'maven'
    }

    stages {
      stage('checkout'){
        steps {
            checkout scm
        }
      }
      stage('compile'){
        steps {
            sh 'mvn compile'
        }
      }

    }
    post {
          always {
              slackSend channel: 'devops', message: 'jenkins file '
      // One or more steps need to be included within each condition's block.
      }

    }
}
