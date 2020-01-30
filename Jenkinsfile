


pipeline {
    agent any
    stages {
        stage('Build and Push') {
            steps {
                sh "sed -i 's/BUILD_ID/${BUILD_NUMBER}/g' app/index.html"
                sh "cd app && docker build . -t androidleha/blazesite:${BUILD_NUMBER}"
            }
            post {
                success {
                    sh "docker push androidleha/blazesite:${BUILD_NUMBER}"
                }
            }
        }
        stage('Deploy') {
            steps {
                sh "kubectl apply -f deployment/application.yaml"
            }
        }
    }
    post {
        always {
            sh "docker images | grep blazesite"
        }
    }
}

