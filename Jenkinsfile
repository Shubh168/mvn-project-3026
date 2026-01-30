pipeline {
  agent any

  tools {
    jdk 'java-17'
    maven 'maven-3.9.12'
  }

  stages {
    stage('Clean and Build the Application'){
      steps{
        sh 'mvn clean package'
      }
    }

    stage('SonarCloud analysis') {
        steps{
          withSonarQubeEnv('sonarqube-server') {
            sh 'mvn clean package sonar:sonar -Dsonar.projectKey=mvnapp-org1_mvnproject -Dsonar.projectName=mvnproject -Dsonar.organization=mvnapp-org1 -Dsonar.host.url=https://sonarcloud.io -Dsonar.token=947a1bb99ee3b51823fe4306e0949efc8ad064cd -X'
          }
        }
    }
  }
}