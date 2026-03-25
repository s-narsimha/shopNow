pipeline {
    agent any

    environment {
        AWS_ACCOUNT_ID = "975050024946"
        AWS_REGION = "us-west-1"

        FRONTEND_REPO = "${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_REGION}.amazonaws.com/hari/frontend/capstone"
        BACKEND_REPO  = "${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_REGION}.amazonaws.com/hari/backend/capstone"
        ADMIN_REPO    = "${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_REGION}.amazonaws.com/hari/admin/capstone"
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/s-narsimha/shopNow'
            }
        }

        stage('Build Docker Images') {
            steps {
                sh '''
                echo "Building Docker Images..."
                docker build -t frontend ./frontend
                docker build -t backend ./backend
                docker build -t admin ./admin
                '''
            }
        }

        stage('Login to ECR') {
            steps {
                sh '''
                echo "Logging into ECR..."
                aws ecr get-login-password --region $AWS_REGION | \
                docker login --username AWS --password-stdin $AWS_ACCOUNT_ID.dkr.ecr.$AWS_REGION.amazonaws.com
                '''
            }
        }

        stage('Tag Images') {
            steps {
                sh '''
                echo "Tagging images..."
                docker tag frontend:latest $FRONTEND_REPO:latest
                docker tag backend:latest $BACKEND_REPO:latest
                docker tag admin:latest $ADMIN_REPO:latest
                '''
            }
        }

        stage('Push to ECR') {
            steps {
                sh '''
                echo "Pushing images to ECR..."
                docker push $FRONTEND_REPO:latest
                docker push $BACKEND_REPO:latest
                docker push $ADMIN_REPO:latest
                '''
            }
        }
    }
}
