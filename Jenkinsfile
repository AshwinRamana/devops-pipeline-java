pipeline{
    agent any
    environment {
      JAVA_VERSION="11"
      DEVOPS_BATCH="AUG2022"
    }
    parameters {
      choice(name: 'DEPLOYMENT_ENV', choices: ['UAT1', 'UAT2', 'PREPROD'], description: 'select env for deploy')
      string(name: 'DUMMYSTR', description: 'just a dummy value', defaultValue: 'ashwin')
    }
    triggers { pollscm('*****') }

    options {
      buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '2', numToKeepStr: '2')
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
