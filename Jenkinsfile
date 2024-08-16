pipeline {
    agent any
    environment {
    }
    stages {
                stage('Setup parameters') {
            steps {
                script { 
                    properties([
                        parameters([
                            choice(
                                choices: ['admin', 'worker', client], 
                                name: 'service'
                            ),
                            string(
                                defaultValue: '', 
                                name: 'stack', 
                            )
                        ])
                    ])
                }
            }
        }
        stage('Delete Previous-Stack') { 
            steps {
                script {
                    if (params.service == 'admin') {
                        echo 'I only execute on the master branch'
                        aws cloudformation delete-stack --capabilities CAPABILITY_IAM --stack-name ${params.stack}
                    }
                }
            }
        }
        stage('Release new-Stack') {
            steps {
                script {
                    if (params.service == 'admin') {
                        aws cloudformation create-stack --capabilities CAPABILITY_IAM --stack-name ${params.stack} --template-body file://./apigateway.yml
                    }
                }
            }
        }
    }
}
