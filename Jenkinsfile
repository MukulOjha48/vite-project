pipeline {
    agent any
    stages {
        stage('Build') {
            agent {
                dockerContainer {
                    image 'node:22.11.0-alpine3.20'
                    args '-u root'
                    reuseNode true
                }
            }
            steps {

                step('cleanup repository') {
                    cleanWs()
                }
                step('build') {
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
}