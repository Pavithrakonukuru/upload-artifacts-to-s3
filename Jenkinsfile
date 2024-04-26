pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = 'your-region'
        BUCKET_NAME = 'depali'
        FILE_PATH = 'C:\Users\91956\Desktop\kp-jenkins\upload s3 artifacts\s3_bucket.yaml'
    }

    stages {
        stage('Deploy CloudFormation Stack') {
            steps {
                script {
                    sh "aws cloudformation deploy --stack-name MyS3BucketStack --template-file s3_bucket_template.yaml --parameter-overrides BucketName=${BUCKET_NAME} --capabilities CAPABILITY_IAM"
                }
            }
        }

        stage('Upload Objects to S3') {
            steps {
                script {
                    sh "aws s3 cp ${FILE_PATH} s3://${BUCKET_NAME}/"
                }
            }
        }
    }

    post {
        always {
            // Cleanup actions if needed
        }
    }
}