pipeline {
  agent any    
  }
  stages {
    stage('Read Dockerfile') {
      steps {
        sh 'cat DockerFile'
        readFile 'Dockerfile'
      }
    }
    stage('Build') {
      steps {
        echo 'We are going to build our image docker !'
        sh 'docker build -t solene/installtv2 .'
      }
    }
    stage('Test') {
      steps {
        echo 'We will test if the build run with 3 type of DB'
      }
    }
    stage('Testpostgresql') {
      steps {
        parallel(
          "Test": {
            echo 'Starting  run test'
            
          },
          "Testmysql": {
            echo 'Starting  run test with mysql'
            
          },
          "Testqlite": {
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

