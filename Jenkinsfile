pipeline {
  agent any
  tools {
    maven 'M2_HOME'
  }
  environment {
    registry="kengne/devops-pipeline"
    registryCredential="DockerID"
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
          sh 'docker build -t myimage' + ':' + $registryCredential
          sh 'docher push $registry' 
      }
    }
  }
}
