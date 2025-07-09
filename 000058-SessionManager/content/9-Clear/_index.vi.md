---
title : "Dọn dẹp tài nguyên"
date : 2023-10-25 
weight : 9 
chapter : false
pre : " <b> 9. </b> "
---

1. Dọn dẹp dịch vụ IAM

    + Tại thanh tìm kiếm, nhập IAM
    + Tại trang dịch vụ IAM, bên trái thanh Navigation Panel chọn Role
    + Tại trang Roles, tìm kiếm Lambda, tích chọn Lambda
    + Bấm button Delete, nhập tên Role: LambdaAnalyzeRole
![Clear](/images/8.Clear/clearIAM.jpg)
![Clear](/images/8.Clear/clearIAM1.jpg)
![Clear](/images/8.Clear/clearIAM2.jpg)

2. Dọn dẹp dịch vụ Lambda
    
    + Tại thanh tìm kiếm, nhập Lambda
    + Tại trang dịch vụ Lambda, bên trái thanh Navigation Panel chọn Function
    + Tích chọn **ProcessInventoryData**
    + Chọn **Actions**, chọn **Delete**
    + Tại **Delete function**, nhập **confirm**

![Clear](/images/8.Clear/clearlambda.jpg)
![Clear](/images/8.Clear/clearlambda1.jpg)
![Clear](/images/8.Clear/clearlambda2.jpg)

3. Dọn dẹp dịch vụ DynamoDB
    + Tại thanh tìm kiếm, nhập DynamoDB
    + Tại trang dịch vụ DynamoDB, bên trái thanh Navigation Panel chọn Table
    + Tích chọn **Iventory**
    + Chọn **Delete**, nhập **confirm**

![Clear](/images/8.Clear/cleardb.jpg)
![Clear](/images/8.Clear/cleardb1.jpg)
![Clear](/images/8.Clear/cleardb2.jpg)

4. Dọn dẹp dịch vụ S3
    + Tại thanh tìm kiếm, nhập S3
    + Tại trang dịch vụ S3, bên trái thanh Navigation Panel chọn General purpose buckets
    + Tích chọn **iot-log-2025**
    + Chọn **Empty**. nhập **permanently delete**
    + Chọn **Delete**, nhập **iot-log-2025**

![Clear](/images/8.Clear/clears3.jpg)
![Clear](/images/8.Clear/clears3_1.jpg)
![Clear](/images/8.Clear/clears3_2.jpg)
![Clear](/images/8.Clear/clears3_3.jpg)
![Clear](/images/8.Clear/clears3_4.jpg)

5. Dọn dẹp AWS IoT Core
    + Tại thanh tìm kiếm, nhập AWS IoT Core
    + Tại trang dịch vụ AWS IoT Core, bên trái thanh Navigation Panel chọn Things
    + Chọn **InventorySensor1**
    + Chọn **Delete**, nhập **InventorySensor1**

![Clear](/images/8.Clear/clearIoT.jpg)
![Clear](/images/8.Clear/clearIoT2.jpg)
![Clear](/images/8.Clear/clearIoT3.jpg)

+ Tại Tại trang dịch vụ AWS IoT Core, bên trái thanh Navigation Panel chọn Rules
    + Chọn **InventoryRule**
    + Chọn **Delete**, nhập **InventoryRule**
    
![Clear](/images/8.Clear/clearIoT4.jpg)
![Clear](/images/8.Clear/clearIoT5.jpg)

+ Tại Tại trang dịch vụ AWS IoT Core, bên trái thanh Navigation Panel chọn Policies
    + Chọn **IoTInventoryPolicy**
    + Chọn **Delete**, nhập **IoTInventoryPolicy**

![Clear](/images/8.Clear/clearIoT6.jpg)
![Clear](/images/8.Clear/clearIoT7.jpg)

+ Tại Tại trang dịch vụ AWS IoT Core, bên trái thanh Navigation Panel chọn Certificates
    + Chọn **7fa53e8ed2f2f2f0937741775116a7061656dc2ff0b7b66c33085435a223a63e**
    + Chọn **Action**, chọn **Delete**, nhập **delete**

![Clear](/images/8.Clear/clearIoT8.jpg)
![Clear](/images/8.Clear/clearIoT9.jpg)
