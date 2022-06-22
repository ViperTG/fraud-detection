# CONFIGURE THE ENVIRONMENT
In this step, you will create an S3 bucket, upload files to the s3 bucket and use a CloudFormation (CFN) template to deploy the infrastructure for this workshop. AWS CloudFormation simplifies provisioning the infrastructure, so we can concentrate on tasks related to data migration.




## Bucket Creation
1. Open the AWS S3 console, and click on Create Bucket in the right-hand corner.

2. Enter a bucket name-it must be unique! Note down your bucket name as you will need to enter this bucket name in a subsequent step. Scroll to the bottom and click Create Bucket in lower right corner.

3. Once the bucket is created, find the bucket in the list of buckets and click the link to open the bucket. From the Objects tab of the s3 console, click on the Upload button.

4. In the next step, files will be Uploaded to the newly created S3 bucket. Download these files to your device so they can be uploaded to S3 in the next step. Using the Download Linked Files option works well. These are the necessary files:

    **Asset** resource：[solnday_cfn.json](solnday_cfn.json)

    **Asset** resource：[lambda-functions.zip](lambda-functions.zip)

    **Asset** resource：[PythonKafkaSink.zip](lPythonKafkaSink.zip)

5. Upload the files to the S3 bucket. Click on Add files and follow the interface to upload the files including clicking the Upload button.
6. Upload the files to the S3 bucket. Click on Add files and follow the interface to upload the files including clicking the Upload button.
7. Select Template is ready, and choose Upload a template file as the source template. Then, click on Choose file and upload the [solnday_cfn.json](solnday_cfn.json). Click Next.
8. Populate the form as with the values specified below, and then click Next.



   Stack Name:  A unique identifier without spaces using only lower case letters.

   BucketName:  The s3 bucket name created above. This parameter is only the bucket name itself and can not have a folder. Do not user the URL or the s3 prefix. Only the bucket name

   KeyName:  The KeyPair (ee-default-keypair.pem) that you created in the previous step.

   SourceIPAddr:  The IP address range allowed access to the public subnet. This can be changed to only access your current IP address. In this case change this paramater to /32. One way to get your IP address is to place http://checkip.amazonaws.com in a browser window. It will return your IP address.

9. On the Stack Options page, accept all of the defaults and click Next.

10. On the Review page, Select the button saying I acknowledge that AWS CloudFormation might create IAM resrouces. Then, click Create stack.

11. At this point, you will be directed back to the CloudFormation console and will see a status of CREATE_IN_PROGRESS. Please wait here until the status changes to COMPLETE

12. Once CloudFormation status changes to CREATE_COMPLETE, go to the Outputs section.

13. Make a note of the Output values from the CloudFormation environment that you launched as you will need them for the remainder of the tutorial:




