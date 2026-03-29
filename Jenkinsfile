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
    stage('Build & Push docker image'){
      steps{
        script{
          withDockerRegistry(credentialsId: 'docker') {
            sh '''
        docker build -t tirupati .
        docker tag tirupati tirupatipallu/java1:29.03
        docker push tirupatipallu/java1:29.03
        '''
        }
        }
      }
    }
    stage('Check Port') {
            steps {
                script {
                    def portStatus = sh(script: 'netstat -tuln | grep ":9000"', returnStatus: true)
                    if (portStatus == 0) {
                        echo "Port 9000 is in use, stopping and removing the existing container"
                        sh 'docker stop aseem_container'
                        sh 'docker rm aseem_container'
                    } else {
                        echo "Port 9000 is available"
                    }
                }
            }
        }
    stage('Deploy Container'){
      steps{
        sh 'docker run -d -p 9000:8080 --name Tirupati_app tirupatipallu/java1:29.03'
      }
    }
  }
}
