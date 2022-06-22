# CONFIGURE AWS SERVICES

Now that you have completed setting up the workshop enviornment, there are just a few more steps so the services communicate with each other. These steps will configure Kinesis to use managed streaming for Kafka and allow viewing the Kafka topics through a viewer interface.

These are the services that will be used:

1. Amazon Managed Streaming for Apache Kafka (Amazon MSK)
2. Amazon DynamoDB
3. Amazon Kinesis
4. AWS CloudFormation

The environment for this lab consists of:

An EC2 instance with kafdrop.
Kafdrop is a web UI for viewing Kafka topics and browsing consumer groups. The tool displays information such as brokers, topics, partitions, consumers, and lets you view messages.
In addition to the EC2 instance and networking components, the provided CloudFormation script creates the following AWS resources

A Managed Streaming for Kafka (MSK) cluster

A Kinesis Data Anayltics application

A DynamoDB fraud audit table

![arch](FraudFlinkDynamoArchitecture.jpeg)

## Kafka Topics
1. Demo_transactions: Topic to hold sample transactions (populated by Lambda SampleTransactionGenerator)
This topic should have transaction as sample transaction lambda function was started by the cloud formation script

2. Flagged_accounts: Topic to hold flagged account Ids (populated by Lambda FlagAccountGenerator)
Initially, this topic will be empty as we need to manually run the lambda function to generate flagged acounts

3. Processed_topic: Topic to hold flagged transactions (populated by flink application)
Initially, this topic will also be empty but will become populated once the sample transaction can successfully join with Flagged Accounts


## MANAGED STREAMING FOR KAFKA
In this section, Managed Streaming for Kafka will be used to find the Kafka bootstrap servers to use in working with the Analytic flink application.

1. Go to the Managed Streaming for Kafka console interface. Navigate to the MSK Clusters page. If you end up on the main page instead of the clusters page, click on the three dashes on the upper left corner of the page to reveal the navigation to the clusters page. Finally, click on the MSK cluster name created by the startup script.

MSK navigationMSK navigation 2MSK navigation 3

2. o get the bootstrap servers needed for later connection to this Kafka cluster, Click on View Client Information

MSK view client

3. Click on the copy icon to the left of the plaintext version of the bootstrap servers.

Get bootstrap servers



These bootstrap servers will be needed for the next step. For safe keeping, save the bootstrap servers to a text file.

## KINESIS DATA ANALYTICS
In this section, Kinesis Data Analytics the Kafka bootstrap servers will be entered into the properties for the Kinesis data analytics application so the application can connect to Kafka.

1. Go to the Kinesis Data Analytics console interface. Click on Kineis Data Analytics Application created by the CloudFormation script.


2. On the Data Analytics application page, click on Configure


3. Scroll down to the Networking section on the same page. Under VPC Connectivity click on the radio button to select VPC configuration based on Amazon MSK cluster. Choose the MSK cluster.


4. Scroll down to Runtime properties on this page. Paste the bootstrap servers into the Value column for the bootstrap.servers


5. Scroll down to the bottom and click Save Changes . It will initiate update to the configuration and take you back to Data Analytics application page.

6. Once it finish applying updates, On the Data Analytics application page, click on Run


7. Click Run




