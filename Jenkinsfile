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
       /var/lib/jenkins/kubectl version --short --client
       '''
     }
   }
    stage("eks deployment") { 
      steps {
      sh '''
      sudo aws sts get-caller-identity
      sudo aws eks update-kubeconfig --region ap-south-1 --name practice-eks
      sudo aws eks list-clusters
      sudo /var/lib/jenkins/kubectl get nodes 
      #sudo /var/lib/jenkins/kubectl create namespace srinu
      sudo /var/lib/jenkins/kubectl apply -f deployment.yml -n srinu
      sudo /var/lib/jenkins/kubectl get pods -n srinu
      '''
      }
    }
  }
}
