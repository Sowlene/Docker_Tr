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
  }
}