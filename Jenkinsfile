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
    stage("Build"){
      steps{
       bat 'mvn install'
      }
    }
    stage("Unit Test"){
      steps{
       bat 'mvn test'
      }
    }
    stage("SonarQube"){
      steps{
        withSonarQubeEnv("test sonar"){
          bat 'sonar-maven-plugin:3.9.1.2184:sonar'
        }
      }
    }
  }
}
