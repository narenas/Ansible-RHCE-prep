pipeline {
    agent {
        node {
            label 'nico-pc'
        }
    }
    options {
        buildDiscarder(logRotator(numToKeepStr: '5'))
    }
    parameters {
        string(defaultValue: "3" , name: "VAGRANT_NUM_NODES")
    }
    stages {
        stage('Build Vagrant env') {
            steps {
                sh '''
                    cd vagrant
                    vagrant destroy -f
                    VAGRANT_NUM_NODES=${params.VAGRANT_NUM_NODES} vagrant up 
                '''
            }
            post {
                failure {
                    sh '''
                        cd vagrant
                        vagrant destroy -f
                    '''
                }
            }
        }
        stage('Destroy environment') {
            steps {
                sh '''
                    cd vagrant
                    vagrant destroy -f
                '''
            }
        }
    }
}