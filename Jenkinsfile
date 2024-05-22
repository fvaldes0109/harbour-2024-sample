pipeline {
    agent any
    tool name: 'go-1.22', type: 'go'

    stages {
        stage('Build') {
            steps {
                sh 'go build main.go'
                sh 'ls -la'
                sh 'echo "Build done!!!"'
            }
        }
    }
}
