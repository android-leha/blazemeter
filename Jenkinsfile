


pipeline {
    agent any
    stages {
        stage('Build and Push') {
            steps {
                sh "sed -i 's/BUILD_ID/${BUILD_NUMBER}/g' app/index.html"
                sh "cd app && docker build . -t androidleha/blazesite:${BUILD_NUMBER} -t androidleha/blazesite"
            }
            post {
                success {
                    withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                        sh "docker login -u $USERNAME -p $PASSWORD"
                        sh "docker push androidleha/blazesite"
                    }
                }
                cleanup {
                    sh "docker logout"
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

