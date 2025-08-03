pipeline {
    agent any
    environment {
        AWS_DEFAULT_REGION = 'us-east-1'
	    S3_BUCKET = 's3-deploy-lsbr'
    }
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Najeme/s3-deploy.git'
            }
        }
        
   /* stage('install AWS CLI (option)'){
        steps {
               sh '''
                   curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
                    sudo apt install unzip
                    unzip awscliv2.zip
                    sudo ./aws/install
               '''
          }
      }*/
    stage('Upload to S3') {
        steps {
                withCredentials([[ $class: 'AmazonWebServicesCredentialsBinding', credentialsId: 'my_aws_credential']]){
                sh '''
		        aws configure set aws_access_key_ID %AWS_ACCESS_KEY_ID%
		        aws configure set aws_secret_access_key %AWS_SECRET_ACCESS_KEY%
                aws s3 cp . s3://s3-deploy-lsbr --recursive 
                '''
		}
            }
        }
    }
}