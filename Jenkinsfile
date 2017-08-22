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
            sh 'cd Debian_Dev/ && docker build -t solene/installtv2 .'
            
          }
        )
      }
    }
    stage('Run') {
      steps {
        parallel(
          "Run": {
            echo 'Run'
            
          },
          "Postgresql": {
            echo 'Run with Postgresql'
            
          },
          "Mysql": {
            echo 'Run with Mysql'
            
          },
          "Sqlite": {
            echo 'Run with PSqlite'
            
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