pipeline {
    agent any

    tools {
        go 'go-1.22'
        nodejs 'nodejs-22'
    }

    stages {
        stage('Build') {
            steps {
                sh 'go build main.go'
                sh 'ls -la'
                sh 'echo "Build done!!!"'
            }
        }

        stage('Deploy to Stage') {
            environment {
                ANSIBLE_HOST_KEY_CHECKING = 'false'
            }
            steps {
                sh 'echo "Deploying..."'
                ansiblePlaybook credentialsId: 'mykey2',
                                inventory: 'stage.ini',
                                playbook: 'playbook.yml'
            }
        }

        stage('E2E Test - Stage') {
            steps {
                sh 'echo "Running E2E tests on Stage..."'
                sh 'newman run e2e-test.json --environment stage.json'
            }
        }

        stage('Deploy to Production') {
            environment {
                ANSIBLE_HOST_KEY_CHECKING = 'false'
            }
            steps {
                sh 'echo "Deploying..."'
                ansiblePlaybook credentialsId: 'mykey2',
                                inventory: 'prod.ini',
                                playbook: 'playbook.yml'
            }
        }

        stage('E2E Test - Production') {
            steps {
                sh 'echo "Running E2E tests on Production..."'
                sh 'newman run e2e-test.json --environment production.json'
            }
        }
    }
}
