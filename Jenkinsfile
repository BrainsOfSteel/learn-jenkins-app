pipeline {
    agent any

    stages {
        stage('Build') {
            agent { 
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    rm -rf node_modules
                    npm install
                    #npm run build
                    ls -la
                '''
            }
        }

        stage('Test') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }

            steps {
                sh '''
                    rm -rf node_modules
                    npm install react-scripts --save-dev
                    npm test
                '''
            }
        }
    }
}
