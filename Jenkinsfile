pipeline {
    agent any
    environment {
        AWS_DEFAULT_REGION = 'us-west-2'
        BUCKET_NAME = 'sashi'
        OBJECT_KEY = 's3_yaml'
        LOCAL_FILE_PATH = 'C:\\Users\\91956\\Desktop\\demo\\s3_bucket.yaml'
    }
    stages {
        stage('Deploy CloudFormation Stack') {
            steps {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'Nani', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
                    script {
                        sh "aws cloudformation deploy --template-file s3_bucket.yaml --stack-name my-s3-stack --parameter-overrides BucketName=${BUCKET_NAME} ObjectKey=${OBJECT_KEY} LocalFilePath=${LOCAL_FILE_PATH} --capabilities CAPABILITY_IAM"
                    }
                }
            }
        }
    }
}
