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
      steps {
        junit 'peikang_result'
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