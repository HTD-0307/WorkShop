---  
title : "Create SNS"  
date : 2023-10-25  
weight : 5  
chapter : false  
pre : " <b> 5. </b> "  
---  

#### Create SNS  
1. Access the [SNS service management interface](https://console.aws.amazon.com/sns/home)  
 + Click **Topic**.  
 + Click **Create topic**.  

![VPC](/images/5.SNS/createSNS1.jpg)  
![VPC](/images/5.SNS/createSNS2.jpg)  

2. On the **Create Topic** page.  
 + In the **Type** section, select **Standard**.  
 + In the **Name** section, enter: **InventoryAlerts**.  
 + Click **Create Topic**.  

![VPC](/images/5.SNS/createSNS3.jpg)  
![VPC](/images/5.SNS/createSNS4.jpg)  

3. Create **Subscriptions**  
 + Click **Subscriptions**  
 + Select **Create Subscriptions**  
![VPC](/images/5.SNS/createSNS7.jpg)

 + When the **Create Subscriptions** section appears  
 + In **Topic ARN**, select **arn:aws:sns:us-east-1:922456364996:InventoryAlerts:f2b3d4d3-794d-42f4-a76e-5974a6514506**  
 + In **Protocol**, select **Email**  
 + In **Endpoint**, enter the email to receive alerts.  
 + Select **Create Subscriptions**  

![VPC](/images/5.SNS/createSNS5.jpg)

 + Check the registered SNS email to activate.  

 ![VPC](/images/5.SNS/createSNS6.jpg)