pipeline {
  agent any
  stages {
    stage('NPM Install') {
      steps {
        sh 'npm install'
            }
        }

    stage('Login into registry') {
    steps {
      withCredentials([string(
                credentialsId: 'npm-token',
                variable: 'NPM_TOKEN')
                ])  {
        sh "echo registry=http://nexus:8081/repository/npm-private/ > .npmrc"
        sh "echo always_auth=true > .npmrc"
        sh "echo _auth=${env.NPM_TOKEN} > .npmrc"
        sh 'npm whoami'
        sh 'cat .npmrc'
        sh 'rm .npmrc'
                }
            }
        }
    }
}
