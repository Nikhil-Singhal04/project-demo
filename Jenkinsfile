pipeline {
    agent any

    environment {
        TF_IN_AUTOMATION = 'true'
    }

    stages {

        stage('Init') {
            steps {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding',
                                  credentialsId: 'AWS-CREDS']]) {
                    sh 'terraform init -no-color'
                }
            }
        }

        stage('Plan') {
            steps {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding',
                                  credentialsId: 'AWS-CREDS']]) {
                    sh 'terraform plan -no-color'
                }
            }
        }

        stage('Apply') {
            steps {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding',
                                  credentialsId: 'AWS-CREDS']]) {
                    sh 'terraform apply -auto-approve -no-color'
                }
            }
        }
    }
}
