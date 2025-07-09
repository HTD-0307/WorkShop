---  
title : "AWS IoT Core Configuration"  
date : 2023-10-25  
weight : 4  
chapter : false  
pre : " <b> 4. </b> "  
---  
  
To receive data from the automatic sensor source, we need to configure AWS IoT Core.  
Access the [AWS IoT Core management console](https://console.aws.amazon.com/iot/home).  
  
1. Create **Thing**  
 + Select **Thing**  
 + Click on **Create thing**  
  
![S3](/images/4.s3/createIoT.jpg)  
  
 + In the **Number of thing to create** section  
 + Select Create single thing  
 + Click **Next**  
  
![S3](/images/4.s3/createIoT1.jpg)  
  
 + When the **Specify thing properties** section appears  
 + In the **Thing name** field, enter **InventorySensor**  
 + Click **Next**  
  
![S3](/images/4.s3/createIoT2.jpg)  
  
 + In the **Device certificate** section, select **Auto-generate a new certificate**  
 + Click **Next**  
  
![S3](/images/4.s3/createIoT3.jpg)  
  
 + Click create thing  
 + Download the files in the **Download certificates and key** table to your device  
  
![S3](/images/4.s3/createIoT4.jpg)

2. Create policies  
 + In the **Security** section, select **Policies**  
 + Choose **Create policy**  
![S3](/images/4.s3/createIoT5.jpg)  

 + In **Policy name**, enter **IoTInventoryPolicy**  
 + In **Policy action**:  
 + Select **iot:Connect**  
 + Select **iot:Publish**  
 + Select **iot:Subscribe**  
 + Select **iot:Receive**  
 + In **Policy resource**, enter **arn:aws:sns:us-east-1:922456364996:InventoryAlerts**  
![S3](/images/4.s3/createIoT7.jpg)  

 + Select **Certificates**  
 + Click on the **Certificates** of the project  
 + Choose **Action** and select **Attach policy**  

![S3](/images/4.s3/createIoT6.jpg)  

 + In **Policies**, select **IoTInventoryPolicy**  
 + Choose **Attach policies**  

![S3](/images/4.s3/createIoT8.jpg)  

 + Continue by selecting **Attach to things**  

![S3](/images/4.s3/createIoT9.jpg)  

 + In **Things**, select **InventorySensor1**  
 + Choose **Attach to thing**  

![S3](/images/4.s3/createIoT10.jpg)

3. Create a rule

 + Select **Message routing**  
 + Select **Rule**  
 + Select **Create rule**  

![S3](/images/4.s3/createIoT11.jpg)  

 + In **Rule name**, enter **InventoryRule**  
 + Select **Next**  

![S3](/images/4.s3/createIoT12.jpg)  

 + In **SQL statement**, enter **SELECT * FROM 'inventory/sensor1/data'**  
 + Select **Next**  

![S3](/images/4.s3/createIoT14.jpg)  

 + In **Action1**, select **Lambda**  
 + In **Lambda function**, select **ProcessInventoryData**  
 + In **Lambda function version**, select **$LATEST**  
 + Select **Next**  

![S3](/images/4.s3/createIoT15.jpg)  

+ Select **Create**  

![S3](/images/4.s3/createIoT13.jpg)  