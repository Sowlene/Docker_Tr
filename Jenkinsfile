pipeline {
  agent any
  stages {
    stage('Welcome') {
      steps {
        parallel(
          "Welcome": {
            echo 'Welcome'
            
          },
          "Situation": {
            sh 'pwd && who && ls -Shal #l not pass'
            
          }
        )
      }
    }
    stage('Build') {
      steps {
        parallel(
          "Build": {
            echo 'Build'
            
          },
          "Autorisation": {
            sh 'ls -lhS /var/run/ | grep docker.sock'
            
          },
          "Build Docker": {
            sh 'docker build -t solene/installtv2 .'
            
          }
        )
      }
    }
    stage('Run') {
      steps {
        echo 'Run'
      }
    }
    stage('End') {
      steps {
        echo 'End'
      }
    }
  }
}