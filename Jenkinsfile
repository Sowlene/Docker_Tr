pipeline {
  agent {
    dockerfile {
      filename 'Dockerfile'
    }
    
  }
  stages {
    stage('Test lecture du DockerFile') {
      steps {
        echo 'Welcome in this step : DockerFile Reading'
      }
    }
    stage('Build de l\'image docker') {
      steps {
        echo 'Step for Testing if build = OK '
        sh 'sudo docker build -t solene/installtv2 .'
      }
    }
  }
}