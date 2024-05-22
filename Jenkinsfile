pipeline {
    agent any

    stages {
        tool name: 'go-1.22', type: 'go'
        stage('Build') {
            steps {
                sh 'go build main.go'
                sh 'ls -la'
                sh 'echo "Build done!!!"'
            }
        }
    }
}
