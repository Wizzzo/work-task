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
        readFile(file: 'package.json', encoding: 'UTF-8')
        script {
          def json = readJSON file:'package.json'
          def version = json.version
          def name = json.name
          echo version
        }

        sh 'zip -r .zip ./'
        sh 'curl -uadmin:AP57BMy9gSebA1RGQee8AvrDe33 -T ./.zip "http://52.209.252.95:8081/artifactory/example-repo-local/.zip"'
      }
    }
  }
}