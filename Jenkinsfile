pipeline {
    agent any
    stages {
        stage('Many tests') {
            parallel {
                stage('Shard #1') {
                    agent {
                        docker {
                            image 'mcr.microsoft.com/playwright:v1.17.1'
                        }
                    }
                    steps {
                        sh 'npx playwright test --shard=1/2'
                    }
                }
                stage('Shard #2') {
                    agent {
                        docker {
                            image 'mcr.microsoft.com/playwright:v1.17.1'
                        }
                    }
                    steps {
                        sh 'npx playwright test --shard=2/2'
                    }
                }
            }
        }
    }
}