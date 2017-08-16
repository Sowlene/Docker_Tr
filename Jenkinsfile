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
            sh 'pwd'
            sh 'ls -lhS /var/run/ '
            sh 'docker build -t solene/installtv2 .'
            
          }
        )
      }
    }
    stage('ContainersStarting') {
      steps {
        echo 'Container are going to start for our test steps :)'
      }
    }
    stage('Test') {
      steps {
        parallel(
          "TestDocker": {
            echo 'We\'re in our testes step, enjoy !'
            
          },
          "TestWithPostgresql": {
            sh 'docker run -i -e DATABASE_TYPE=postgresql -e DATABASE_USER=tracimuser -e DATABASE_PASSWORD=tracimpassword -e DATABASE_HOST=192.168.1.73 -e DATABASE_NAME=tracimdb solene/installtv2'
            
          },
          "TestWithMysql": {
            sh 'docker run  -e DATABASE_TYPE=mysql -e DATABASE_USER=tracimuser -e DATABASE_PASSWORD=tracimpassword -e DATABASE_HOST=192.168.1.73 -e DATABASE_NAME=tracimdb solene/installtv2'
            
          },
          "TestWithsqlite": {
            sh 'docker run -e DATABASE_TYPE=sqlite -e DATABASE_USER=tracimuser -e DATABASE_PASSWORD=tracimpassword -e DATABASE_HOST=192.168.1.73 -e DATABASE_NAME=tracimdb solene/installtv2'
            
          }
        )
      }
    }
    stage('End') {
      steps {
        echo 'Winter is coming. '
      }
    }
  }
}