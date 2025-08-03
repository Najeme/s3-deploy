pipeline {
    agent any
    environment {
        AWS_DEFAULT_REGION = 'us-east-1'
	S3_BUCKET = "s3-deploy-lsbr"
    }
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Najeme/s3-deploy.git'
            }
        }
        stage('Upload to S3') {
            steps {
                sh '/usr/local/bin/aws s3 cp . s3://s3-deploy-lsbr --recursive --exclude ".git/*"'
            }
        }
    }
}