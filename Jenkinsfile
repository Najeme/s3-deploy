pipeline {
    agent any
    environment {
        AWS_ACCESS_KEY_ID = credentials('aws-access-key-id') 
        AWS_SECRET_ACCESS_KEY = credentials('aws-secret-access-key') 
        AWS_DEFAULT_REGION = 'us-east-1'
	    S3_BUCKET = 's3-deploy-lsbr'
    }
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Najeme/s3-deploy.git'
            }
        }
        
    stage('install AWS CLI (option)'){
        steps {
               sh '''
                   curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
                    sudo apt install unzip
                    unzip awscliv2.zip
                    sudo ./aws/install
               '''
          }
      }
    stage('Upload to S3') {
        steps {
                sh 'aws s3 cp . s3://s3-deploy-lsbr --recursive --exclude ".git/*"'
            }
        }
    }
}