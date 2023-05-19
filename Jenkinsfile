pipeline {
  agent { label 'master' }
  stages {
    stage("Initializing") {
      steps {
      echo "this is first stage"
      }
    }
    stage("Docker login") {
      steps {
      sh 'docker --version'
      sh ' Docker login -u -p'
      
      }
    }
   stage("Docker build") {
     steps {
       sh ''''
       docker build -t srinu:latest .
       docker push srinu:latest
       '''
     }
   }
  }
}
