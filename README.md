# aws-s3download-custom
Custom Resources expand the Cloud Formation as you can run custom logic as part of your Cloud Formation Deployment. In this example the CloudFormation template will deploy a lambda function and the function download a file from the url and write the file to Lambda temporary memory and upload the file to S3. The cloudformation template takes the S3 bucket and FileURL as input parameter and download the file from the specified FileURL and put this into the S3 bucket.

<img width="384" alt="image" src="https://github.com/debadatta30/aws-s3download-custom/assets/136390466/11d12aaf-6c6d-46db-954f-c5fe9da909c9">


The ZipFile property used to specify the Lambda Function code ,cfn-response module is used to send the response to the those resources. The module has a send method which send the response object to a custom property. After executing the send method the Lambda function terminates. 

Requirements:

  •	AWS CLI
  
  •	S3 Bucket
  
Upload Template Files to S3 Bucket:

aws s3 cp . s3://my-bucket/downlader/ --recursive

CloudFormation Stack Creation:

aws cloudformation create-stack \
--stack-name downloader \
--template-url https://my-bucket.s3.region.amazonaws.com/downloader/CustomDownloader.yaml \
--capabilities CAPABILITY_NAMED_IAM
