---  
title : "Create Lambda Function"  
date : 2023-10-25  
weight : 1  
chapter : false  
pre : " <b> 3.1. </b> "  
---  

1. Access the [Lambda service management interface](https://console.aws.amazon.com/lambda/home).  
 + Click on **Create Function**.  

![Connect](/images/3.connect/createlambda.jpg)  

2. On the Create function page.  
 + Click on **Author from scratch**.  
 + In the **Function name** field, enter **ProcessInventoryData**.  
 + In the **runtime** field, select **python 3.9**.  
 + In the **Execution role** field, select **Use an existing role**.  
 + In the **Existing role** field, select the role created in IAM earlier.  

![Connect](/images/3.connect/createlambda1.jpg)  

3. Scroll to the bottom of the page and select **Create function**.  
![Connect](/images/3.connect/createlambda2.jpg)  