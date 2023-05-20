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
      sh ' sudo Docker login -u srinivasulumudduluru -p Subbamma@2233#'
      
      }
    }
   stage("Docker build") {
     steps {
       sh ''''
       sudo docker build -t srinivasulumudduluru/srinu:latest .
       sudo docker push srinivasulumudduluru/srinu:latest
       '''
     }
   }
  }
}
