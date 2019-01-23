pipeline {
  agent any
  stages {
    stage('commitlint') {
      steps {
        sh 'npm install -g commitlint'
        sh 'nodenv rehash'
        sh 'commitlint --config=commitlint.config.json .'
      }
    }
  }
}
