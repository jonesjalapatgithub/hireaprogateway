pipeline {
    agent any
    stages {
        stage('Delete Previous-Stack') { 
            steps {
                    sh "aws cloudformation delete-stack --stack-name hireaproapigateway5"
                }
            }
        stage('Release new-Stack') {
            steps {
                    sh "aws cloudformation create-stack --stack-name hireaproapigateway --template-body file://./apigateway.yml"
                }
            }
        }
}
