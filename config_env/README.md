# CONFIGURE THE ENVIRONMENT
In this step, you will create an S3 bucket, upload files to the s3 bucket and use a CloudFormation (CFN) template to deploy the infrastructure for this workshop. AWS CloudFormation simplifies provisioning the infrastructure, so we can concentrate on tasks related to data migration.




## Bucket Creation
1. Open the AWS S3 console, and click on Create Bucket in the right-hand corner.

2. Enter a bucket name-it must be unique! Note down your bucket name as you will need to enter this bucket name in a subsequent step. Scroll to the bottom and click Create Bucket in lower right corner.

3. Once the bucket is created, find the bucket in the list of buckets and click the link to open the bucket. From the Objects tab of the s3 console, click on the Upload button.

4. In the next step, files will be Uploaded to the newly created S3 bucket. Download these files to your device so they can be uploaded to S3 in the next step. Using the Download Linked Files option works well. These are the necessary files:

    **Asset** resource：[solnday_cfn.jason](solnday_cfn.json)
    **Asset** resource：[lambda-functions.zip](lambda-functions.zip)
    **Asset** resource：[PythonKafkaSink.zip](lPythonKafkaSink.zip)





