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
            sh 'docker build .'
            
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