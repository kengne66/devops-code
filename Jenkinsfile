pipeline {
  agent any
  tools {
    maven 'M2_HOME'
  }
  environment {
    registry="kengne/devops-pipeline"
    registryCredential="DockerID"
    dockerImage = ''
  }
  stages {
    stage( 'Build' ){
      steps {
        sh 'mvn clean'
        sh 'mvn install'
        sh 'mvn package'
      }
    }
     stage( 'test' ){
      steps {
       sh 'mvn test'
      }
    }
     stage( 'deploy' ){
      steps {
        script {
         docker.withRegistry( '', registryCredential ) {
          dockerImage.push("$BUILD_NUMBER")
          dockerImage.push('latest')
         }
        }
      }
    }
  }
}
