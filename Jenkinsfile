pipeline {
    agent any 
    stages {
        stage('Build Docker Image') {
            steps {
                echo 'Hello world'
                sh "docker build . -t mahesh/web:$IMAGE_TAG"
                echo 'Build Successfully'
            }
        }
    }
}
