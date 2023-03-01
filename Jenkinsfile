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
    stage("Build"){
      steps{
       bat 'mvn clean'
      }
    }
    stage("Test"){
      steps{
       bat 'mvn test'
      }
    }
    stage("SonarQube"){
      steps{
        withSonarQubeEnv("test sonar"){
          bat 'mvn sonar:sonar'
        }
      }
    }
    stage("Upload to Artifactory"){
      steps{
        rtMavenDeployer(
            id:'deployer',
            serverId:'123456789@artifactory',
            releaseRepo:'arpan.nagptest',
            snapshotRepo:'arpan.nagptest'
        )
        rtMavenRun(
            pom:'pom.xml',
            goals: 'clean install',
            deployerId: 'deployer'
        )
        rtPublisherBuildInfo(
            serverId:'123456789@artifactory'
        )
      }
    }
  }
}
