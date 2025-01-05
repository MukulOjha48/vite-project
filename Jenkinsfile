pipeline {
    agent any
    options {
        skipDefaultCheckout(true)
    }
    stages {
        stage('cleanup') {
            steps {
                cleanWs()
            }
        }

        stage('checkout') {
            steps {
                checkout scm 
            }
        }

        stage('Build') {
            agent {
                dockerContainer {
                    image 'node:22.11.0-alpine3.20'
                }
            }
            steps {
                    sh '''
                    ls -l
                    node --version
                    npm --version
                    npm install
                    npm run build
                    ls -l
                    '''
                }
            }
        } 
    }