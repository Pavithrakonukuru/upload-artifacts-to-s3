pipeline {
    agent any
    environment {
        AWS_DEFAULT_REGION = 'your-aws-region'
        BUCKET_NAME = 'my-example-bucket'
        OBJECT_KEY = 'example.txt'
        LOCAL_FILE_PATH = 'path/to/local/file.txt'
    }
    stages {
        stage('Deploy CloudFormation Stack') {
            steps {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'Nani', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
                    script {
                        sh "aws cloudformation deploy --template-file path/to/your/template.yml --stack-name my-s3-stack --parameter-overrides BucketName=${BUCKET_NAME} ObjectKey=${OBJECT_KEY} LocalFilePath=${LOCAL_FILE_PATH} --capabilities CAPABILITY_IAM"
                    }
                }
            }
        }
    }
}
