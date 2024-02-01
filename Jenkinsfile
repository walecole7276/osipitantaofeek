pipeline {
    agent any
    stages {
        stage('Print Parameters') {
            steps {
                sh '''
                echo "Hello World!!"
                aws cloudformation list-stacks
                '''
            }
        }
    }
}
