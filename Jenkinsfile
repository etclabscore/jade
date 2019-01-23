pipeline {
  agent any
  stages {
    stage('') {
      steps {
        sh 'git --no-pager log --pretty=format:%s -n 1 HEAD~1 | docker run --rm -i gtramontina/commitlint:7.3.2'
      }
    }
  }
}