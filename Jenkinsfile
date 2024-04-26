pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = 'your-region'
        BUCKET_NAME = 'depali'
        STACK_NAME = 'my-s3-bucket-stack'
        FILE_PATH = "C:\\Users\\91956\\Desktop\\kp-jenkins\\upload s3 artifacts\\s3_bucket.yaml"
        TEMPLATE_FILE = 's3_bucket.yaml'
    }

    stages {
        stage('Deploy CloudFormation Stack') {
            steps {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'Nani', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
                    script {
                        sh "aws cloudformation deploy --template-file $TEMPLATE_FILE --stack-name $STACK_NAME --parameter-overrides BucketName=${params.BucketName} --capabilities CAPABILITY_IAM"
                    }
                }
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