pipeline {
    agent any
    stages {
        stage('Print Parameters') {
            steps {
                sh '''
                echo "Hello World!!"
                aws s3api create-bucket \
                    --bucket newmy-bucket56 \
                    --region us-east-1
                '''
            }
        }
    }
}
