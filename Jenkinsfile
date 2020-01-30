


pipeline {
    agent any
    stages {
        stage('Build and upload') {
            steps {
                sh "cd app && docker build . -t blazesite"
            }
        }
    }
}

