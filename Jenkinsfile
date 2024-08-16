pipeline {
    agent any
    environment {
    }
    stages {
        stage('Delete Previous-Stack') { 
            steps {
                    sh "aws cloudformation delete-stack --capabilities CAPABILITY_IAM --stack-name hireapro-gateway"
                }
            }
        }
        stage('Release new-Stack') {
            steps {
                    sh "aws cloudformation create-stack --capabilities CAPABILITY_IAM --stack-name hireapro-gateway
 --template-body file://./apigateway.yml"
                }
            }
        }
    }
}
