pipeline {
  agent any
  stages {
    stage('Docker Build') {
      steps {
        sh 'docker build -t apasoft/jenkins-web:latest .'
      }
    }
    stage('Docker Push') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'xx', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
          sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
          sh 'docker push apasoft/jenkins-web:latest'
        }
      }
    }
  }
}