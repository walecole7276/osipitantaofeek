pipeline {
    agent any

    environment {
        AWS_REGION = 'us-east-1'
        BUCKET_NAME = 'my-unique-s3-bucket-yu6546name'
    }

    stages {
        stage('Deploy S3 Bucket') {
            steps {
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding', 
                    credentialsId: 'MyAwsCred', // Use the ID from the previous step
                    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY'
                ]]) {
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
