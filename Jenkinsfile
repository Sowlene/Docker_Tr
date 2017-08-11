pipeline {
  agent {
    dockerfile {
      filename 'Dockerfile'
    }
    
  }
  stages {
    stage('error') {
      steps {
        parallel(
          "sqlite": {
            sh 'docker run -it -p 80:80 -e DATABASE_TYPE=sqlite -e DATABASE_USER=tracimuser -e DATABASE_PASSWORD=tracimpassword -e DATABASE_HOST=192.168.1.73 -e DATABASE_NAME=tracimdb solene/installtv2'
            
          },
          "postgresql": {
            sh 'docker run -it -p 80:80 -e DATABASE_TYPE=postgresql -e DATABASE_USER=tracimuser -e DATABASE_PASSWORD=tracimpassword -e DATABASE_HOST=192.168.1.73 -e DATABASE_NAME=tracimdb solene/installtv2'
            
          },
          "mysql": {
            sh 'docker run -it -p 80:80 -e DATABASE_TYPE=mysql -e DATABASE_USER=tracimuser -e DATABASE_PASSWORD=tracimpassword -e DATABASE_HOST=192.168.1.73 -e DATABASE_NAME=tracimdb solene/installtv2'
            
          }
        )
      }
    }
  }
}