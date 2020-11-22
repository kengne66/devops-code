pipeline {
  agent any
  tools {
    maven 'M2_HOME'
  }
  environment {
    registry="kengne/devop-pipeline"
    registryCredential="DockerID1"
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
          docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
     stage( 'docker' ){
      steps {
        echo "image steps"
        sleep 10
      }
    }
  }
}
