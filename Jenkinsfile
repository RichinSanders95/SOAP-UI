pipeline {
  agent any
  tools { 
      maven 'Maven363' 
      jdk 'JDK20' 
  }
  stages {
    stage('Checkout') {
      steps {
        // Checkout the code from Github
        git 'https://github.com/RichinSanders95/SOAP-UI.git'
      }
    }
    stage('Build') {
      steps {
        // Build the project with Maven
        sh 'mvn clean verify'
      }
    }
    stage('Publish Test Results') {
      steps {
        // Publish the test results to Jenkins
        junit '/Users/richin/.jenkins/workspace/API Automation/target/surefire-reports/*.xml'
      }
    }
  }
}
