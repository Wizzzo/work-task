pipeline {
  agent any
  stages {
    stage('git clone') {
      steps {
        git(url: 'git@github.com:Wizzzo/work-task.git', branch: 'master', credentialsId: 'github-ssh')
      }
    }
    stage('unit tests') {
      steps {
        sh 'npm install'
        sh 'npm run unit:tests'
      }
    }
  }
}