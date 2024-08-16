pipeline {
    agent any
    environment {
    }
    stages {
        stage('Delete Pre-Stack APIGateway') { 
            steps {
                echo "Running ${VERSION} on ${env.JENKINS_URL}"
                sh 'aws cloudformation delete-stack --capabilities CAPABILITY_IAM --stack-name hireapro-gateway' 
            }
        }
        stage('Release new-Stack APIGateway') {
            steps {
                sh "aws cloudformation create-stack --capabilities CAPABILITY_IAM --stack-name hireapro-gateway --template-body file://./apigateway.yml"
            }
        }
    }
}
