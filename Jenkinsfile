pipeline {
    agent any
    stages {
        stage('Print Parameters') {
            steps {
                sh '''
                echo "Hello World!!"
                aws s3api create-bucket \
                    --bucket newmy-bucket5678 \
                    --region us-east-1
                '''
            }
        }
    }
}
