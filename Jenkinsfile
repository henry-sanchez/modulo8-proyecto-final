pipeline {
  agent none
  parameters {
    string defaultValue: 'frontend-docker', description: 'rama de proyecto frontend', name: 'BRANCH', trim: false
    string defaultValue: 'debian', description: 'nodo esclavo en VM', name: 'LABEL_NODE_DEV', trim: false
    string defaultValue: 'debian', description: 'nodo ambiente QA', name: 'LABEL_NODE_QA', trim: false
    string defaultValue: 'master', description: 'nodo Master principal', name: 'LABEL_NODE_PROD', trim: false
  }
  environment{
    DEV_NODE="${params.LABEL_NODE_DEV}"
    QA_NODE="${params.LABEL_NODE_QA}"
    PROD_NODE="${params.LABEL_NODE_PROD}"
  }
  stages {
    stage('cloning') {
      agent { label DEV_NODE }
      steps {
        git branch: "${params.BRANCH}", url: 'https://github.com/janny35/Gestion_tareas_multiusuarios.git'
        sh 'echo "clonación finalizada"'
      }
    }
    stage('deploying in dev') {
      agent { label DEV_NODE }
      steps {
        sh 'docker build -t proyecto-final-front:1.0.0 .'
      }
    }
  }
}