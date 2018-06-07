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
            junit 'target/surefire-reports/*.xml'
          }
        }
        stage('walter_cov') {
          steps {
            cobertura(coberturaReportFile: 'target/site/cobertura/coverage.xml')
          }
        }
      }
    }
    stage('end') {
      steps {
        archiveArtifacts 'target/*.jar'
        sh 'mvn package'
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