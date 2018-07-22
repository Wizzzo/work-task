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
        sh 'npm run test:unit'
      }
    }
    stage('upload artifact to artifactory') {
      steps {
        sh 'curl -uadmin:AP57BMy9gSebA1RGQee8AvrDe33 -T <PATH_TO_FILE> "http://52.209.252.95:8081/artifactory/example-repo-local/'
        sh '''zip -r my_arch.zip my_folder
echo jsonSlurper'''
      }
    }
  }
}