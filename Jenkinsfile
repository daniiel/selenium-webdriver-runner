pipeline{
  agent any
  stages{
    stage("Start Grid") {
      steps{
        sh "docker-compose up -d hub chrome firefox"
      }
    }
    stage("Run Test") {
      steps{
        sh "docker-compose up search-module book-flight-module"
      }
    }
    stage("Stop Grid") {
      steps{
        sh "docker-compose down"
      }
    }
  }
  post{
    always{
      archiveArtifacts artifacts: 'output/**'
      sh "docker-compose down"
    }
  }
}
