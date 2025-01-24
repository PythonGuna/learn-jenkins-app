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
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
        stage('test') {
            steps {
                sh '''
                    grep -f /var/jenkins_home/workspace/fromhit/build/index.html
                    npm test
                '''
            }
        }
    }
}