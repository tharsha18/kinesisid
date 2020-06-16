# Lab1 : Stream ingest AWS IOT Core data to Amazon Kinesis Streams

1.	Sign in to the AWS IoT console using the instructions your lab instructor has provided
2.	Search for AWS IOT Core under services menu. 
   On the left hand side, expand "Manage" --> click "Things" --> create -->   Create a single thing --> name anything like "myIOTTopic". (A thing represents a device that will send the data to IOT for processing and storage)
    
    Alternatively, you an run the following AWS CLI command and go tp step 3.
    `aws iot create-thing --thing-name myIoTTopic`

3.	
  If you used AWS CLI command to create a "thing", then find the certificates in the screenshot below. Otherwise, skip the following screenshot and move on to selecting the certificate. 
  
  ![screenshot](imglab1/Picture1.png)
 
  Click create certificate as seen in screenshot below.
  
  ![screenshot](imglab1/Picture2.png)
 
  Download all the files and click activate as seen in screenshot below
  
  ![screenshot](imglab1/Picture3.png)

   Don't miss the 4th cert CA root cert at the bottom of the page and download the cert named "Amazon Root CA 1"

•	Create IoT Core policy
o	Navigate to Secure --> Policies on the left hand pane and click create apolicy. Enter any name and add 2 actions as follows and click create. To create a second section, click Add Statement button

 ![screenshot](imglab1/Picture4.png)

 
•	Attach policy to certificate
o	Navigate to Secure--> certificates pane on IOT core landing page, click on the certificate you created previously. In the top right corner, click on the menu represnted by ... and select attach policy. Select the policy you just created and click attach.
 
![screenshot](imglab1/Picture5.png)
 

•	Attach certificate to thing
Navigate back to the certificates page, select the certificate you created previously. From the same menu represented by ... , select Attach thing. Select the thing you created previously.
 
![screenshot](imglab1/Picture6.png)

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

