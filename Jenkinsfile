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
            readFile 'Dockfile'
            
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