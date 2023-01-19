pipeline {
    agent any
    stages {
        stage('Many tests') {
            parallel {
                stage('Shard #1') {
                    agent {
                        docker {
                            image 'mcr.microsoft.com/playwright:v1.29.0-focal'
                        }
                    }
                    steps {
                        sh "npm install"
                        sh 'npx playwright test --shard=1/2'
                    }
                }
            }
        }
    }
}