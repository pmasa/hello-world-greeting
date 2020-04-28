pipeline {
 environment {
 registry = "pedromasa/webapp"
 registryCredential = 'dockerhub'
 dockerImage = ''
 } 
agent any
 stages {
  stage('Poll') {
   steps{
     checkout scm
    }
   }
  stage('Build & Unit test'){
   steps{
        sh 'mvn clean verify -DskipITs=true';
        junit '**/target/surefire-reports/TEST-*.xml'       
    }
   }
   stage('Static Code Analysis'){
    steps{
        sh 'mvn clean verify sonar:sonar -Dsonar.projectName=example-project -Dsonar.projectKey=example-project -Dsonar.projectVersion=$BUILD_NUMBER';
     }
    }
   stage ('Integration Test'){
    steps{
        sh 'mvn clean verify -Dsurefire.skip=true'; 
        junit '**/target/failsafe-reports/TEST-*.xml'
     }
   }
   stage ('Publish'){
    steps{

        }
    }
   }
}
