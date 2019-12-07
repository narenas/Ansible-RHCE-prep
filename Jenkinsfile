pipeline {
  agent {
    node {
      label 'nico-pc'
    }

  }
  stages {
    stage('Build Vagrant env') {
      steps {
        sh '''cd vagrant
vagrant up 
'''
      }
    }

    stage('Destroy environment') {
      steps {
        sh 'vagrant destroy'
      }
    }

  }
}