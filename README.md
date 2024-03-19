AT83.03 CLOUD COMPUTING

Set-Up Instructions for Cloud-Based Video Processing Platform:

1. Amazon Simple Storage Service (S3)
     - Create a source and destination bucket in S3.
     - Configure the source bucket for Cross-Origin Resource Sharing. (see CORS_S3Bucket file)
2. IAM Role for Lambda Function
     - Create IAM Role and attach policies that grants access to S3. In this case since we
       are working with Amazon S3 and Elastic Transcoder, attach the 'AmazonS3ReadOnlyAccess' and
       'AmazonElasticTranscoderJobsSubmitter' policies.
     - Create inline policy for S3 Bucket. (see IAM_S3Policy file)
3. AWS Lambda Function
     - Create Lambda function and choose the IAM Role created in the previous step. (see Lambda-Transcoder file)
     - Add trigger and choose the source bucket in the S3, and event type to 'PUT'. This will
       trigger the function every time a file is uploaded in the S3 bucket.
4. Amazon Elastic Transcoder
     - Create a pipeline and select the input (source) and output (destination) buckets respectively.
     - Take note of the pipeline ID to be configured in the Lambda function.

     
