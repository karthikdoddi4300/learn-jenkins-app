pipeline {
    agent any

    stages {
        /*
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
                ls -la  
                '''
            }
            
        }
        */
        
        stage('test'){
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps{
               sh'''
               #test -f build/index.html
               #npm test
               echo 'test stage'
            '''
            }
        }
    
        stage('E2E'){
            agent{
                docker{
                    image 'mcr.microsoft.com/playwright:v1.39.0-jammy'
                    reuseNode true
                   // args '-u root:root' 
                }
            }
            steps{
               sh'''
               npm install  serve
               node_modules/.bin/serve -s  build &
               sleep 10
               npx playwright test
              
            '''
            }
        }
    }
    post{
        always{
            junit 'jest-results/junit.xml'
        }
    }
}
