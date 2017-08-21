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
        dir(path: '/var/lib/jenkins/workspace/Sowlene_Docker_Tr_master-BKNB6FCY5LJARIWM7QM33SLIQXAUMZFX6H7O3WOAIWZETDJQEIOQ/Debian_Dev/')
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