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

        stage('Deploy') {
            steps {
                sh 'echo "Deploying..."'

                withCredentials([string(credentialsId: 'mykey', variable: 'mykey')]) {
                    echo "And the key is: ${mykey}"

                    sh "echo '${mykey}' > ./mykey"

                    // sh 'chmod 600 ./mykey'

                    sh 'scp -i ./mykey main maksymprokopov@192.168.105.3:'
                }


            }
        }
    }
}
