pipeline {
  agent any
  stages {
    stage('checkout project') {
      steps {
        checkout scm
      }
    }
    stage('peikang_test_shell') {
      steps {
        sh 'mvn cobertura:cobertura test'
      }
    }
    stage('walter_report') {
      parallel {
        stage('walte_report') {
          steps {
            sh 'target/surefire-reports/*.xml'
          }
        }
        stage('walter_cov') {
          steps {
            cobertura(coberturaReportFile: 'target/site/cobertura/coverage.xml')
          }
        }
      }
    }
  }
  post {
    always {
      echo 'I will always say Hello again!'

    }

    success {
      echo 'success!'

    }

    failure {
      echo 'failure!'

    }

  }
}