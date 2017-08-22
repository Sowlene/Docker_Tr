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
            sh 'docker run -e DATABASE_TYPE=postgresql -e DATABASE_USER=tracimuser -e DATABASE_PASSWORD=tracimpassword -e DATABASE_HOST=192.168.1.73 -e DATABASE_NAME=tracimdb solene/docker_trac_dev'
            
          },
          "Mysql": {
            echo 'Run with Mysql'
            sh '''cd Debian_Dev/ docker run -e TEST_DATABASE_ENGINE=mysql solene/docker_trac_dev
'''
            
          },
          "Sqlite": {
            echo 'Run with PSqlite'
            sh 'docker run -e DATABASE_TYPE=sqlite -e DATABASE_USER=tracimuser -e DATABASE_PASSWORD=tracimpassword -e DATABASE_HOST=192.168.1.73 -e DATABASE_NAME=tracimdb solene/docker_trac_dev'
            
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