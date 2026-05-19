pipeline {
    agent any

    stages {
        stage('build') {
            agent{
                docker{
                    image 'node:18-alpine'
                }
            }
            steps {
                sh '''
                npm install
                npm run build
                ls -l
                '''
            }
        }
        stage('test'){
            agent{
                docker{
                    image 'node:18-alpine'
                }
            }
            steps{
                sh ''' 
                    npm run test
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