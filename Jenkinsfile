pipeline {
    agent {
        dockerContainer {
            image 'node:18-alpine'
        }
    }
    stages {
        stage('Build') {
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