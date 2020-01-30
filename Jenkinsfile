


pipeline {
    agent any
    stages {
        stage('Build and upload') {
            steps {
                sh "sed -i 's/BUILD_ID/${BUILD_NUMBER}/g' app/index.html"
                sh "cd app && docker build . -t localhost:5000/blazesite:${BUILD_NUMBER} -t blazesite"
                sh "docker push localhost:5000/blazesite:${BUILD_NUMBER}"
            }
        }
    }
    post {
        always {
            sh "docker images | grep blazesite"
        }
    }
}

