pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps { 
                script{
                 app = docker.build("underwater")
                }
            }
        }
        stage('Test'){
            steps {
                 echo 'Empty'
            }
        }
        stage('Deploy') {
            steps {
                script{
                        docker.withRegistry('https://033115095740.dkr.ecr.us-east-1.amazonaws.com', 'ecr:us-east-1:aws-credentials') {
                    app.push("${env.BUILD_NUMBER}")
                    app.push("latest")
                    }
                }
            }
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
