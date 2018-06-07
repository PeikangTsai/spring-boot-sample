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
    stage('peikang_report') {
      parallel {
        stage('peikang_report') {
          steps {
            junit 'peikang_result'
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