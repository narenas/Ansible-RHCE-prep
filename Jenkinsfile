pipeline {
    agent {
        node {
            label 'nico-pc'
        }
    }
    options {
        buildDiscarder(logRotator(numToKeepStr: '5'))
    }
    stages {
        stage('Build Vagrant env') {
            steps {
                sh '''
                    cd vagrant
                    vagrant destroy -f
                    vagrant up 
                '''
            }
            post {
                failure {
                    sh '''
                        cd vagrant
                        vagrant -f destroy
                    '''
                }
            }
        }
        stage('Destroy environment') {
            steps {
                sh '''
                    cd vagrant
                    vagrant -f destroy
                '''
            }
        }
    }
}