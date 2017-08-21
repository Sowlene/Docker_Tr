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
            sh 'pwd && who && ls -Shal #l not pass'
            
          }
        )
      }
    }
    stage('Change Directory') {
      steps {
        parallel(
          "Change Directory": {
            sh 'cd Debian_Dev/ && pwd'
            
          },
          "": {
            sh 'ls -Shal'
            
          }
        )
      }
    }
    stage('Situation') {
      steps {
        sh 'cat Dockerfile'
      }
    }
    stage('Build Docker Image') {
      steps {
        parallel(
          "Build Docker Image": {
            sh 'ls -lhS /var/run/ | grep docker.sock'
            
          },
          "Build": {
            sh 'docker build -t solene/installtv2 .'
            
          }
        )
      }
    }
    stage('End') {
      steps {
        echo 'End '
      }
    }
  }
}