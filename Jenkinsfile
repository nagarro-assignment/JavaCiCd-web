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
          bat(script: 'mvn sonar:sonar', label: 'upload analysis to sonar')
        }

      }
    }

    stage('sonar gate check') {
      steps {
        waitForQualityGate true
      }
    }
    
    stage('push to artifactory') {
      steps {
        bat(script: 'mvn deploy')
      }
    }
  }
}