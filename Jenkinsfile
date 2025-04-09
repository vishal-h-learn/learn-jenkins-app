pipeline {
    agent {
        docker {
                    image "node:18-alpine"
                    reuseNode true
                }
        }

    stages {
        stage('Cleanup') {
            steps {
                cleanWS()
            }
        }
        stage('Build') {
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
        stage('Test') {
            steps {
                sh '''
                    echo "Test Stage"
                    test -f build/index.html
                    npm test
                    '''
            }
        }
    }
}
