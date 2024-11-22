pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/m-manu619/frontend-repo.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build Frontend') {
            steps {
                sh 'npm run build'
            }
        }
        stage('Deploy to S3') {
            steps {
                withAWS(credentials: 'aws-credentials-id', region: 'ap-south-1') {
                    sh 'aws s3 sync ./build s3://ecommerce-frontend-bucket-demo --delete'
                }
            }
        }
    }
}
