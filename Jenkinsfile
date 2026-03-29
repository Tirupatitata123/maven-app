pipeline {
  agent any
  tools {
    maven 'maven'
  }
  stages {
    stage ('Git Checkout'){
      steps{
        git branch: 'main',url: 'https://github.com/Tirupatitata123/maven-app.git'

        echo 'CHeckout successfully...'
      }
    }
    stage('Build stage'){
      steps{
        sh 'mvn clean package'
      }
    }
    stage('Building docker image'){
      steps{
        sh 
        '''docker build -t tirupati .
        docker tag tirupati tirupatipallu/java1:29.03
        docker push tirupatipallu/java1:29.03
        '''
      }
    } 
  }
}
