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
            sh 'cd Debian_Dev/ && docker build -t solene/docker_trac_dev .'
            
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
            sh 'cd Debian_Dev/ && docker run -e TEST_DATABASE_ENGINE=postgresql solene/docker_trac_dev'
            
          },
          "Mysql": {
            echo 'Run with Mysql'
            sh 'cd Debian_Dev/ && docker run -e TEST_DATABASE_ENGINE=mysql solene/docker_trac_dev'
            
          },
          "Sqlite": {
            echo 'Run with PSqlite'
            sh 'cd Debian_Dev/ && docker run -e TEST_DATABASE_ENGINE=sqlite solene/docker_trac_dev'
            
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