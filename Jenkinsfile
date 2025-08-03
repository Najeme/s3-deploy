pipeline {
    agent any
    environment {
        AWS_DEFAULT_REGION = 'us-east-1'
	S3_BUCKET = "s3-deploy-lsbr"
    }
    stage {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Najeme/s3-deploy.git'
            }
        }
        
    stage('install AWS CLI (option)'){
        steps {
               bat '''
	       aws --version || (
                   curl -o awscliv2.zip https://awscli.amazonaws.com/AWSCLIV2.msi
                   msiexec.exe /i awscliv2.zip /quiet
               )
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