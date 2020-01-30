


pipeline {
    agent any
    stages {
        stage('Build and upload') {
            steps {
                sh "sed -i 's/BUILD_ID/${BUILD_NUMBER}/g' index.html"
                sh "cd app && docker build . -t blazesite:${BUILD_NUMBER}"
            }
        }
    }
    post {
        always {
            sh "docker images"
        }
    }
}

