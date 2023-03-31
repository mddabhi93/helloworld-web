pipeline {
    agent any 
    stages {
        stage('Build Docker Image') {
            steps {
                echo 'Hello worl'
                sh "docker build . -t mahesh/nginx:latest"
                sh "docker run -p 8000:8000 -it mahesh/nginx:latest"
            }
        }
    }
}
