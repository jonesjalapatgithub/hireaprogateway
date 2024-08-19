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
                    sh "aws cloudformation create-stack --capabilities CAPABILITY_IAM --stack-name hireaproapigateway --template-body file://./apigateway.yml"
                }
            }
        }
}
