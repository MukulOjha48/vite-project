pipeline {
    agent any

    environment {
        VERCEL_TOKEN = credentials('VERCEL_TOKEN')
    }
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
                docker {
                    image 'node:22.11.0-alpine3.20'
                    args '-u root'
                    reuseNode true
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

        stage('Deploy') {
            agent {
                docker {
                    image 'node:22.11.0-alpine3.20'
                    args '-u root'
                    reuseNode true
                }
            }
            steps {
                sh ''' 
                    npm install -g vercel
                    vercel --prod --token=$VERCEL_TOKEN --confirm --name=viteproject
                
                '''
            }
        }
    } 
}