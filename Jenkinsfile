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
        sh 'cd Debian_Dev/ && ls -Shal'
      }
    }
    stage('Situation') {
      steps {
        findFiles(glob: 'Dockerfile')
        readFile 'Dockerfile'
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