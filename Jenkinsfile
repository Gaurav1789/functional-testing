
pipeline {
     agent any
  tools {
    maven "MVN3"
  }
  
  stages {
    stage('pullscm') {
      steps {
        git branch: 'main', credentialsId: 'github', url: 'git@github.com:Gaurav1789/functional-testing.git'
      }
    }
    stage('execute test') {
      steps {
        sh "mvn clean test"
      }
         post {
              success {
                   publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'TestReport', reportFiles: 'TestReport.html', reportName: 'FunctionalTestReport', reportTitles: '', useWrapperFileDirectly: true])
              }
         }
    }
  }
}
