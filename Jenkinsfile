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
