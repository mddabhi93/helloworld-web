pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps { 
                 echo 'Test Done and updated'
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
                  sh 'aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 557831573860.dkr.ecr.us-east-1.amazonaws.com'
                  sh 'docker build -t web-app .'
                  sh 'docker tag web-app:latest 557831573860.dkr.ecr.us-east-1.amazonaws.com/web-app:latest'
                  sh 'docker push 557831573860.dkr.ecr.us-east-1.amazonaws.com/web-app:latest'
                    }
            }
        }
        stage('Build Docker Image') {
            steps {
                echo 'Hello world'
                sh "aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 557831573860.dkr.ecr.us-east-1.amazonaws.com"
                sh "docker build -t web-app ."
                sh "docker tag web-app:latest 557831573860.dkr.ecr.us-east-1.amazonaws.com/web-app:latest"
                sh "docker push 557831573860.dkr.ecr.us-east-1.amazonaws.com/web-app:latest"
                echo 'Build Successfully'
            }
        }
    }
}
