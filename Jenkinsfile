pipeline {
    agent any
    stages {
        stage('Print Parameters') {
            steps {
                sh '''
                echo "Hello World!!"
                aws cloudformation create-stack --stack-name testter --template-body file://Animals4Life.yml --region us-east-1
                '''
            }
        }
    }
}
