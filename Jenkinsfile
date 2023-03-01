pipeline{
  agent any
  tools{
     maven 'Maven'
  }
  stages{
    stage("Checkout"){
      steps{
        checkout scm
      }
    }
    stage("Build & Test"){
      steps{
       bat 'mvn clean test'
      }
    }
    stage("SonarQube"){
      steps{
        withSonarQubeEnv("test sonar"){
          bat 'mvn sonar:sonar'
        }
      }
    }
  }
}
