pipeline {
    agent {
        docker {
            image 'node:18-alpine'
            reuseNode true
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