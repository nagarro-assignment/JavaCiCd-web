pipeline {
  agent any
  stages {
    stage('compile') {
      steps {
        bat 'mvn compile'
      }
    }

    stage('sonar analysis') {
      steps {
        bat 'mvn sonar:sonar -Dsonar.projectKey=JavaProjectCiCd-web -Dsonar.host.url=http://localhost:9000 -Dsonar.login=4ae577b8a88a9bbbf12efc21f50543ab20148f4e'
      }
    }

  }
}