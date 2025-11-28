pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh 'npm install'
      }
    }

    stage('Test') {
      steps {
        sh 'node --version'
      }
    }

    stage('Docker publish') {
      environment {
        registry = 'eduardsie/tesestingnode'
        registryCredential = 'dockerhub_id'
      }
      steps {
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }

      }
    }

  }
}