pipeline{
  agent any
  tools{
     maven 'Maven'
  }
  stages{
    stage("Checkout"){
      steps{
        bat 'mvn --version'
        checkout scm
      }
    }
    stage("Build and Test"){
      steps{
       bat 'mvn clean test'
      }
    }
    stage("SonarQube"){
      steps{
        withSonarQubeEnv("arpan-sonar-tokens"){
          bat 'mvn clean package sonar:sonar'
        }
      }
    }
  }
}
