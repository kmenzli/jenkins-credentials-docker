pipeline {
  agent {
    docker {
      image 'node:18.16.0-alpine'
      label 'docker'
    }
  }
  stages {
     stage('Docker check') {
      steps {
        sh 'node --version'
      }
    }
    stage('Docker Build') {
      steps {
        sh 'docker build -t kmenzli/jenkins-web:latest .'
      }
    }
    stage('Docker Push') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'docker', passwordVariable: 'dockerPassword', usernameVariable: 'dockerUser')]) {
          sh "docker login -u ${env.dockerUser} -p ${env.dockerPassword}"
          sh 'docker push kmenzli/jenkins-web:latest'
        }
      }
    }
  }
}
