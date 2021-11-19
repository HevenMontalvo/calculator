pipeline {
  agent any
  stages {
    stage('Compile') {
      steps {
        sh "./gradlew compileJava"
      }
    }
    stage('Unit test') {
      steps {
        sh "./gradlew test"
      }
    }
    stage("Code coverage") {
      steps {
        sh "./gradlew jacocoTestReport"
        publishHTML (target: [
               reportDir: 'build/reports/jacoco/test/html',
               reportFiles: 'index.html',
               reportName: "JaCoCo Report"
          ])
        sh "./gradlew jacocoTestCoverageVerification"
      }
    }
  /*  stage("Static code analysis") {
      steps {
        sh "./gradlew checkstyleMain"
        publishHTML (target: [
          reportDir: 'build/reports/checkstyle/',
          reportFiles: 'main.html',
          reportName: "Checkstyle Report"
          ])
      }
    } */
  /*    stage('Static code analysis sonarqube') {
        steps {
          sh "./gradlew -Dsonar.host.url=http://localhost:9000 sonarqube -Dsonar.login=7fbb817f937e1a4d72889e2252ec47f1bff76872"
        }
      } */

  }
}
