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
    stage('Test') {
      steps {
        // Execute the SoapUI tests
        sh 'mvn soapui:test'
      }
    }
    stage('Publish Test Results') {
      steps {
        // Publish the test results to Jenkins
        junit 'target/soapui-output/*.xml'
      }
    }
  }
}
