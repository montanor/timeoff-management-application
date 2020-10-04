pipeline {
  agent any
  stages {
    stage('NPM Install') {
      steps {
        sh 'npm install'
      }
    }

    stage('Publish Artifact') {
      steps {
        sh 'npm publish'
      }
    }

  }
}