pipeline {
    agent {
        docker {
            image 'mcr.microsoft.com/playwright:v1.54.2-jammy'
        }
    }

    options {
        ansiColor('xterm')
    }

    stages {
        stage('install') {
            steps {
                sh 'npm ci'
            }
        }

        stage('build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('unit tests') {
            steps {
                sh 'npx vitest run --reporter=verbose'
            }
        }

        stage('integration test') {
            steps {
                sh 'npx playwright test'
            }
        }

        stage('deploy') {
            steps {
                echo 'Mock deployment was successful!'
            }
        }
    }
}