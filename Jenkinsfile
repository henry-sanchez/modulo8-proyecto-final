pipeline {
  agent {label 'debian'}
  stages {
    stage('cloning') {
      steps {
        git branch: 'frontend-docker', url: 'https://github.com/janny35/Gestion_tareas_multiusuarios.git'
      }
    }
    stage('build') {
      steps {
        sh 'docker ps'
      }
    }
  }
}