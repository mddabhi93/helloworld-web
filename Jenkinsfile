pipeline {
    agent any 
    stages {
        stage('Build Docker Image') {
            steps {
                echo 'Hello world'
                sh "aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 033115095740.dkr.ecr.us-east-1.amazonaws.com"
                sh "docker build -t web-app ."
                sh "docker tag web-app:latest 033115095740.dkr.ecr.us-east-1.amazonaws.com/web-app:latest"
                sh "docker push 033115095740.dkr.ecr.us-east-1.amazonaws.com/web-app:latest"
                echo 'Build Successfully'
            }
        }
    }
}
