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
        withSonarQubeEnv('Default') {
          bat(script: 'mvn compile package', label: 'package')
          bat 'mvn sonar:sonar'
        }

      }
    }

    stage('quality gate') {
      steps {
        waitForQualityGate true
      }
    }

  }
}