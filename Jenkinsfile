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
            sh 'who '
            sh 'cd /home/solene/Applications/docktest/ && ls -lh'
            sh 'chmod 777 /var/run/docker.sock'
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