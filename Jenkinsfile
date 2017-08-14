pipeline {
  agent any
  stages {
    stage('Welcome') {
      steps {
        parallel(
          "Welcome": {
            echo 'Welcome'
            
          },
          "First": {
            readFile 'Dockerfile'
            sh 'cat Dockerfile'
            
          }
        )
      }
    }
    stage('Build') {
      steps {
        parallel(
          "Build": {
            echo 'We are trying to build'
            
          },
          "ImageBuild": {
            sh 'who && chown -Rf solene /var/run/docker.sock '
            sh 'cd /home/solene/Applications/docktest/ && ls -lh'
            sh 'docker build -t solene/installtv2 .'
            
          }
        )
      }
    }
    stage('End') {
      steps {
        echo 'End is finally here.'
      }
    }
  }
}