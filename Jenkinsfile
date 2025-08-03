pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building The Code Example'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing The Application Example'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying The Application Example To S3 bucket'
                sh 'aws s3 cp https://github.com/Najeme/s3-deploy.git s3://s3-deploy-lsbr --recursive'
            }
        }
    }
}