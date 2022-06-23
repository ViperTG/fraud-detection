# FRAUD DETECTION

A customer can be flagged for a variety of reasons determined by the business. This customer may have recently changed their telephone, changed their name, or changed their address. On its own, there is nothing wrong with any of these actions. However, these account activities in combination with large transactions need to be reviewed as a fraud risk. To represent this change, a flagged customer topic will be created and we will write a record to this flagged customer topic. 

In this section, we will generate flagged customers and transactions against the flagged customers. The flagged customers and the transactions will go into separate kafka topics. Using the Kinesis Data Analytics application, these topics will be joined to create a flagged transactions topic.

# Kafka Topics

              * Demo_transactions.
                  * Topic to hold sample transactions (populated by Lambda SampleTransactionGenerator)
                  * This topic should have transaction as sample transaction lambda function was started by the cloud formation script
          
              * Flagged_accounts
                  * Topic to hold flagged account Ids (populated by Lambda FlagAccountGenerator)
                  * Initially, this topic will be empty as we need to manually run the lambda function to generate flagged acounts
          
              * Processed_topic
                 * Topic to hold flagged transactions (populated by flink application)
                 * Initially, this topic will also be empty but will become populated once the sample transaction can successfully join with Flagged Accounts




# Verify Kafka Demo Transactions

## Steps
1. Open a browser window using http://1.2.3.4:9000 NOTE: Substitute 1.2.3.4 with the public IP address obtained from the EC2 Instance.

2. Explore the kafdrop interface to see messages in the following topics:

3. Click on the demo_transactions topic

4. Note the Last Offset is greater than zero showing there are messages in this topic. Click on View Messages

5. Click on the Search for View Messages


# Create Flagged Transactions 


## Steps
1. Go to the AWS Lambda. Click on the link for the ‘FlagAccountGenerator’ lambda function.

2. From the Function interface, Click on the Function name FlagAccountGenerator.py. This will display the python code for this lambda function. Click on the test button and select the Configure test event drop down.

3. Enter an Event name of helloworld and click Create.

4. From the Test Drop Down, Select helloworld

5. Click the Test button to execute the FlagAccountGen function.

#  Verify Kafka Processed Transactions

## Steps
1. Open a browser window using http://1.2.3.4:9000 NOTE: Substitute 1.2.3.4 with the public IP address obtained from the EC2 Instance.

2. Explore the kafdrop interface to see messages in the following topics:

3. Click on the flagged_customers topic

4. Note the Last Offset is greater than zero showing there are messages in this topic. Click on View Messages

5. Click on the Search for View Messages
