pipeline {
  agent any    
  }
  stages {
    stage('Read Dockerfile') {
      steps {
        sh '''echo PATH = ${PATH} && echo M2_HOME = ${M2_HOME}


&& mvn clean'''
        readFile 'Dockerfile'
      }
    }
    stage('Build') {
      steps {
        echo 'Build step !'
        sh 'docker build -t solene/installtv2 .'
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
          "error": {
            sh 'echo PLOP'
            
          }
        )
      }
    }
    stage('END') {
      steps {
        parallel(
          "END": {
            echo 'Image Buid correctly'
            
          },
          "REPORT": {
            archiveArtifacts 'target /* .README.md'
            
          }
        )
      }
    }
  }
}
