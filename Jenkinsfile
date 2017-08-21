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
            echo 'We are trying to build'
            
          },
          "ImageBuild": {
            sh '''ls -lhS /var/run/ | grep docker.sock
'''
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
            sh 'docker run --entrypoint bash solene/installtv2 -c ls -lisa /var/lib/jenkins/workspace/Sowlene_Testdocker_master-PYO76PG2MVGEIIOJ3RJCE7EOHZTFGO7XLVV32IOJYUTNYG42QINA/entrypoint.sh -e DATABASE_TYPE=postgresql -e DATABASE_USER=tracimuser -e DATABASE_PASSWORD=tracimpassword -e DATABASE_HOST=192.168.1.73 -e DATABASE_NAME=tracimdb '
            
          },
          "TestWithsqlite": {
            sh 'docker run --entrypoint bash solene/installtv2 -c ls -lisa /var/lib/jenkins/workspace/Sowlene_Testdocker_master-PYO76PG2MVGEIIOJ3RJCE7EOHZTFGO7XLVV32IOJYUTNYG42QINA/entrypoint.sh -e DATABASE_TYPE=sqlite -e DATABASE_USER=tracimuser -e DATABASE_PASSWORD=tracimpassword -e DATABASE_HOST=192.168.1.73 -e DATABASE_NAME=tracimdb '
            
          },
          "TestWithMysql": {
            sh 'docker run --entrypoint bash solene/installtv2 -c ls -lisa /var/lib/jenkins/workspace/Sowlene_Testdocker_master-PYO76PG2MVGEIIOJ3RJCE7EOHZTFGO7XLVV32IOJYUTNYG42QINA/entrypoint.sh -e DATABASE_TYPE=mysql -e DATABASE_USER=tracimuser -e DATABASE_PASSWORD=tracimpassword -e DATABASE_HOST=192.168.1.73 -e DATABASE_NAME=tracimdb '
            
          }
        )
      }
    }
    stage('End') {
      steps {
        echo 'I will check containers'
        sh 'docker ps'
      }
    }
  }
}