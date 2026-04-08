pipeline {
    agent any

    environment {
        AWS_ACCESS_KEY_ID = credentials('aws-creds').username
        AWS_SECRET_ACCESS_KEY = credentials('aws-creds').password
    }

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/your-repo/terraform-jenkins-project.git'
            }
        }

        stage('Terraform Init') {
            steps {
                sh 'terraform init'
            }
        }

        stage('Terraform Plan') {
            steps {
                sh 'terraform plan'
            }
        }

        stage('Terraform Apply') {
            steps {
                sh 'terraform apply -auto-approve'
            }
        }
    }
}
