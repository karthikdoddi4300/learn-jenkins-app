pipeline {
    agent any

    stages {
        stage('build') {
            agent {
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                node --version
                npm version
                npm ci 
                npm run build
                
               
                '''
            }
        }
        stage('test'){
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps{
            sh'''
            echo "test stage"
            test -f  build/index.html
            npm test
            '''
            }
        }
    }
    post{
        always{
            junit 'test-results/junit.xml'
        }
    }
}
