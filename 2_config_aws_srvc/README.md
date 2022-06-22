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


