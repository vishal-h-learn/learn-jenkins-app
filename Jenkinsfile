pipeline {
    agent any

    stages {
        stage('Build') {
            cleanWs()
            agent{
                docker {
                    image "node:18-alpine"
                    reuseNode true
                }
            }
            steps {
                echo 'Building'
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
    }
}
