pipeline {
  agent { label 'master' }
  environment {
    docker_user = credentials('docker-user')
    docker_password = credentials('docker-passwd')
  }
  stages {
    stage("Initializing") {
      steps {
      echo "this is first stage"
      }
    }
    stage("Docker login") {
      steps {
      sh 'docker --version'
      sh ' sudo docker login -u $docker_user -p $docker_password'
      
      }
    }
   stage("Docker build") {
     steps {
       sh '''
       pwd
       ls
       sudo docker build -t srinivasulumudduluru/srinu:latest .
       sudo docker push srinivasulumudduluru/srinu:latest
       sudo su
       kubectl --version
       '''
     }
   }
  }
}
