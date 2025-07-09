---  
title : "Experimental Results"  
date : 2023-10-25  
weight : 7  
chapter : false  
pre : " <b> 7. </b> "  
---  

1. Run the simulation sensor  
 + Open **Terminal** and navigate to the directory of the file **sensor_simulator.py**  
 + Run the command: **python sensor_simulator.py**  
![Demo](/images/7.Demo/demo1.jpg)  

2. Check data in AWS IoT  
 + Access the [AWS IoT Core management console](https://console.aws.amazon.com/iot/home)  
 + Select **MQTT test client**  
 + In the **Topic filter**, enter **inventory/sensor1/data**  
 + Click **Subscribe**  
 + Click **Publish**  
 + Scroll down to see the data received from the sensor device sent to IoT Core.  

![Demo](/images/7.Demo/demo2.jpg)  
![Demo](/images/7.Demo/demo6.jpg)  

3. Check logs in CloudWatch  
 + Access the [CloudWatch service management interface](https://console.aws.amazon.com/cloudwatch/home)  
 + Select **Log groups**  
 + Choose **/aws/lambda/ProcessInventoryData**  
 + In **Log Stream**, select the most recently updated log stream  
![Demo](/images/7.Demo/demo3.jpg)  
![Demo](/images/7.Demo/demo5.jpg)  

4. Check data in DynamoDB  
 + Access the [DynamoDB service management interface](https://console.aws.amazon.com/dynamodb/home)  
 + Select **Explore items**  
 + Choose the **Inventory** table  
 + Click **Run**; the **Table: Inventory - Items returned** section will contain all the data sent from the sensors.  

![Demo](/images/7.Demo/demo4.jpg)  

5. Check Gmail  

 + Open the Gmail account registered for the SNS service  

![Demo](/images/7.Demo/demo7.jpg)  

SNS will send alerts to the email when a product is received with a quantity lower than 20.