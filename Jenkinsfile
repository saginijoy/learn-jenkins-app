pipeline {
    agent any
    environment{
        BUILD_FILENAME = 'index.html'
    }

    stages {
        stage('Hello') {
             agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                    
                }
            }
            steps {
                echo 'Hello World'
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
        stage('test') {
            steps {
                echo 'Building new git - test'
                sh '''
                test -f build/$BUILD_FILENAME
                '''
            }
        }
    }
}
