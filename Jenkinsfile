pipeline {
  agent {
    dockerfile {
      filename 'Dockerfile'
    }
    
  }
  stages {
    stage('Read Dockerfile') {
      steps {
        sh 'pwd && ls -l'
      }
    }
    stage('Build') {
      steps {
        echo 'Build step !'
        sh '''sudo docker build -t solene/installtv2 .
'''
      }
    }
    stage('Start Testing') {
      steps {
        echo 'We will test if the build run with 3 type of DB'
      }
    }
    stage('Test with postgresql') {
      steps {
        parallel(
          "Test": {
            echo 'Starting  run test'
            
          },
          "Test with mysql": {
            echo 'Starting  run test with mysql'
            
          },
          "Test with sqlite": {
            echo 'Starting  run test with sqlite'
            
          },
          "": {
            sh 'echo PLOP'
            
          }
        )
      }
    }
  }
}