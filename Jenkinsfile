pipeline {
  agent any
  stages {
    stage('Welcome') {
      steps {
        parallel(
          "Welcome": {
            echo 'Here we go'
            
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
          "Autorisations": {
            sh 'ls -lhS /var/run/ | grep docker.sock'
            echo 'Si un message concernant les permissions apparait faites un chmod 770 de ce fichier'
            
          },
          "Build Docker_PROD": {
            sh 'cd Debian_Prod/ && cat Dockerfile && docker build -t solene/docker_trac_dev .'
            
          }
        )
      }
    }
    stage('End') {
      steps {
        echo 'End'
      }
    }
  }
}