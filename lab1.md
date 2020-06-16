# Lab1 : Stream ingest AWS IOT Core data to Amazon Kinesis Streams

1.	Sign in to the AWS IoT console using the instructions your lab instructor has provided
2.	Create a thing. A thing represents a device that will send the data to IOT for processing and storage

`aws iot create-thing --thing-name myIoTTopic`

3.	Register a device
•	Create and activate device certificate
 
 ![screenshot](imglab1/Picture1.png)

 
Download all the files and click activate
 

•	Create IoT Core policy
o	Navigate to Policies and click create. Enter the name and add 2 actions as follows and click create.
 

 
•	Attach policy to certificate
o	Navigate to  the certificates page, click on the certificate you created previously. In the top right corner, click on actions and select attach policy. Select the policy you just created and click attach.
 

 

•	Attach certificate to thing
Navigate back to the certificates page, select the certificate you created previously. From the Actions menu, select Attach thing. Select the thing you created previously.
 


Download rootCA certificate: https://docs.aws.amazon.com/iot/latest/developerguide/server-authentication.html?icmpid=docs_iot_console#server-authentication-certs

4.	Configure device
•	Copy all the certificate files you downloaded previously to a folder from where you will run the simulator that generates random data and sends it to the topic
•	Copy the simulator script to the same folder.
•	Make sure you can access the IOT endpoint from here


5.	Configure and test rules
•	Navigate to Act->Rules and click create
 

•	Enter the name of the rule and update the query to reflect the topic you will be sending data to.
 

•	Navigate down and select Add action. In the next screen, select “Send a message to an Amazon Kinesis Stream” and click configure action
 

















 
•	On the next screen, Select create a new resource for the stream. This will take you to Create a data stream screen.
 

 
•	Click on create data stream and enter the stream name, add the number of shards needed for the use case and click create data stream:

 

 
•	Once the stream is created, go back to the Configure Action page and hit refresh next to Stream Name. You will now see the new stream you just created. Enter the partition key and click on create role.
 
 

•	Enter the role name and click create role:
 


•	Next, click on Add action and you are done with adding a new action to the IOT rule. Now, you are back on Create Rule page. Scroll down and hit Create Rule button. You now have a rule configured to send data to Kinesis Stream. 

6.	Run the simulator script to generate random data to send to AWS IOT Engine.

