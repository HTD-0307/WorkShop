---  
title : "Clean Up Resources"  
date : 2023-10-25  
weight : 9  
chapter : false  
pre : " <b> 9. </b> "  
---  

1. Clean up IAM service  

 + In the search bar, type IAM  
 + On the IAM service page, select Role from the left Navigation Panel  
 + On the Roles page, search for Lambda and check the Lambda box  
 + Click the Delete button, enter the Role name: LambdaAnalyzeRole  
![Clear](/images/8.Clear/clearIAM.jpg)  
![Clear](/images/8.Clear/clearIAM1.jpg)  
![Clear](/images/8.Clear/clearIAM2.jpg)  

2. Clean up Lambda service  

 + In the search bar, type Lambda  
 + On the Lambda service page, select Function from the left Navigation Panel  
 + Check **ProcessInventoryData**  
 + Select **Actions**, then choose **Delete**  
 + In the **Delete function** prompt, type **confirm**  

![Clear](/images/8.Clear/clearlambda.jpg)  
![Clear](/images/8.Clear/clearlambda1.jpg)  
![Clear](/images/8.Clear/clearlambda2.jpg)  

3. Clean up the DynamoDB service  
 + In the search bar, type DynamoDB  
 + On the DynamoDB service page, select Table from the left Navigation Panel  
 + Check **Inventory**  
 + Click **Delete**, enter **confirm**  

![Clear](/images/8.Clear/cleardb.jpg)  
![Clear](/images/8.Clear/cleardb1.jpg)  
![Clear](/images/8.Clear/cleardb2.jpg)  

4. Clean up the S3 service  
 + In the search bar, type S3  
 + On the S3 service page, select General purpose buckets from the left Navigation Panel  
 + Check **iot-log-2025**  
 + Click **Empty**, enter **permanently delete**  
 + Click **Delete**, enter **iot-log-2025**  

![Clear](/images/8.Clear/clears3.jpg)  
![Clear](/images/8.Clear/clears3_1.jpg)  
![Clear](/images/8.Clear/clears3_2.jpg)  
![Clear](/images/8.Clear/clears3_3.jpg)  
![Clear](/images/8.Clear/clears3_4.jpg)  

5. Clean up AWS IoT Core  
 + In the search bar, enter AWS IoT Core  
 + On the AWS IoT Core service page, select Things from the left Navigation Panel  
 + Select **InventorySensor1**  
 + Click **Delete**, enter **InventorySensor1**  

![Clear](/images/8.Clear/clearIoT.jpg)  
![Clear](/images/8.Clear/clearIoT2.jpg)  
![Clear](/images/8.Clear/clearIoT3.jpg)  

 + On the AWS IoT Core service page, select Rules from the left Navigation Panel  
 + Select **InventoryRule**  
 + Click **Delete**, enter **InventoryRule**  

![Clear](/images/8.Clear/clearIoT4.jpg)  
![Clear](/images/8.Clear/clearIoT5.jpg)  

 + On the AWS IoT Core service page, select Policies from the left Navigation Panel  
 + Select **IoTInventoryPolicy**  
 + Click **Delete**, enter **IoTInventoryPolicy**  

![Clear](/images/8.Clear/clearIoT6.jpg)  
![Clear](/images/8.Clear/clearIoT7.jpg)  

+ In the AWS IoT Core service page, select Certificates from the left Navigation Panel.  
+ Select **7fa53e8ed2f2f2f0937741775116a7061656dc2ff0b7b66c33085435a223a63e**.  
+ Click **Action**, select **Delete**, and enter **delete**.  

![Clear](/images/8.Clear/clearIoT8.jpg)  
![Clear](/images/8.Clear/clearIoT9.jpg)