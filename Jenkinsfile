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
      def json = readJSON file:'package.json'
      def version = json.version
      def name = json.name
      steps {
        sh `zip -r ${name}-${version}.zip ./`
        sh `curl -uadmin:AP57BMy9gSebA1RGQee8AvrDe33 -T ./${name}-${version}.zip "http://52.209.252.95:8081/artifactory/example-repo-local/`
      }
    }
  }
}
