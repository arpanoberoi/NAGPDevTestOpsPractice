pipeline{
  agent any
  tools {
        maven 'Maven' 
   }
  stages{
    stage("Checkout"){
      steps{
        sh "mvn --version"
        checkout scm
      }
    }
    stage("Build"){
      steps{
       sh "mvn install"
      }
    }
    stage("Unit Test"){
      steps{
       sh "mvn test"
      }
    }
    stage("SonarQube"){
      steps{
        withSonarQubeEnv("test sonar"){
          sh "org.sonarsource.scanner.maven:sonar-maven-plugin:jar:3.9.1.2184"
        }
      }
    }
  }
}
