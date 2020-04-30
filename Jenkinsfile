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
        
        echo 'Hello, Maven'
           
    }
   }
   stage('Static Code Analysis'){
    steps{
        sh 'mvn sonar:sonar -Dsonar.projectName=ci-project -Dsonar.projectKey=ci-project -Dsonar.projectVersion=$BUILD_NUMBER -Dsonar.host.url=http://192.168.0.114:9000';
     }
    }
   stage ('Integration Test'){
    steps{
        echo 'Hello, SonarQube'
     }
   }

   }
}
