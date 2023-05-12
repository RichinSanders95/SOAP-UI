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
        sh 'mvn clean verify site surefire-report:report'
        sh 'tree'
      }
    }


    // stage('Publish Test Results') {
    //   steps {
    //     // Publish the test results to Jenkins
    //     sh 'mvn surefire-report:report'
    //     // junit '${basedir}/target/surefire-report.html'
    //   }
    // }
  }
  post {
    success {
      publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'target/site', reportFiles: 'surefire-report.html', reportName: 'Surefire Report', reportTitles: '', useWrapperFileDirectly: true])
    }
  }


}
