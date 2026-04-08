pipeline {
    agent any

    environment {
        AWS_CREDS = credentials('aws-creds')
        TF_PLUGIN_TIMEOUT = "60s"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/teluguhackerforfree/terraform-project.git'
            }
        }

        stage('Clean Terraform') {
            steps {
                sh 'rm -rf .terraform .terraform.lock.hcl'
            }
        }

        stage('Terraform Init') {
            steps {
                sh '''
                export AWS_ACCESS_KEY_ID=$AWS_CREDS_USR
                export AWS_SECRET_ACCESS_KEY=$AWS_CREDS_PSW
                terraform init -upgrade
                '''
            }
        }

        stage('Terraform Apply') {
            steps {
                sh '''
                export AWS_ACCESS_KEY_ID=$AWS_CREDS_USR
                export AWS_SECRET_ACCESS_KEY=$AWS_CREDS_PSW
                terraform apply -auto-approve
                '''
            }
        }
    }
}
