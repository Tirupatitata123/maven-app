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
  }
}
