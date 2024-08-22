pipeline {
    agent any
    
    environment {
        AWS_REGION = 'us-east-1' // Specify your AWS region
        BUCKET_NAME = 'my-unique-s3-bucket-name' // Replace with your desired S3 bucket name
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // This is optional if your Jenkinsfile is in your SCM
                    // git branch: 'main', url: 'https://github.com/your-repo/your-project.git'
                    echo 'Checking out code...'
                }
            }
        }

        stage('Deploy S3 Bucket') {
            steps {
                script {
                    echo "Creating S3 bucket: ${BUCKET_NAME} in region ${AWS_REGION}"
                    sh """
                        aws s3api create-bucket \
                            --bucket ${BUCKET_NAME} \
                            --region ${AWS_REGION} \
                            --create-bucket-configuration LocationConstraint=${AWS_REGION}
                    """
                    echo "S3 bucket ${BUCKET_NAME} created successfully."
                }
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully."
        }
        failure {
            echo "Pipeline failed."
        }
    }
}
