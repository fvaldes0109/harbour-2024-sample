pipeline {
    agent any

    tools {
        go 'go-1.22'
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
            steps {
                sh 'echo "Deploying..."'
                ansiblePlaybook credentialsId: 'mykey2',
                                inventory: 'stage.ini',
                                playbook: 'playbook.yml'
            }
        }

        stage('Deploy to Production') {
            steps {
                sh 'echo "Deploying..."'
                ansiblePlaybook credentialsId: 'mykey2',
                                inventory: 'prod.ini',
                                playbook: 'playbook.yml'
            }
        }
    }
}
