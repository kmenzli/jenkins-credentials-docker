pipeline {
  agent any
  stages {
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
