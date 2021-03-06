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
        withCredentials(bindings: [string(
                          credentialsId: 'npm-token',
                          variable: 'NPM_TOKEN')
                          ]) {
            sh 'echo registry=http://nexus:8081/repository/npm-private/ > .npmrc'
            sh 'echo always_auth=true >> .npmrc'
            sh "echo _auth=${env.NPM_TOKEN} >> .npmrc"
            sh 'npm whoami'
            sh 'cat .npmrc'
          }

        }
      }

      stage('Publishing artifact') {
        steps {
          sh 'npm publish'
          sh 'rm .npmrc'
        }
      }

          stage('Deploying into server') {
      steps {
        withCredentials(bindings: [string(
                          credentialsId: 'ansible-asume',
                          variable: 'ROOT_PASS')
                          ]) {
            sh "ansible-playbook -v --inventory=hosts --extra-vars=ansible_sudo_pass=${env.ROOT_PASS} deploytimeoff.yml"
          }

        }
      }

    }
  }
