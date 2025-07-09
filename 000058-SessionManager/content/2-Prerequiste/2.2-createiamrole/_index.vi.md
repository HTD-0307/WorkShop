---
title : "Tạo IAM Role"
date : 2023-10-25 
weight : 2 
chapter : false
pre : " <b> 2.2 </b> "
---

### Tạo IAM Role

Trong bước này chúng ta sẽ tiến hành tạo IAM Role. Trong IAM Role này sẽ được gán policy **Lambda**, đây là policy cho phép Lambda thực thi các hoạt động trong dự án.

1. Truy cập vào [giao diện quản trị dịch vụ IAM](https://console.aws.amazon.com/iamv2/)
2. Ở thanh điều hướng bên trái, click  **Roles**.  

![role](/images/2.prerequisite/createrole.jpg)

3. Click **Create role**.  

![role](/images/2.prerequisite/createrole1.jpg)

4. Click **AWS service** và click **Lambda**. 
  + Click **Next**.  

![role](/images/2.prerequisite/createrole3.jpg)

5. Trong ô Search, điền lần lượt **AWSLambdaExecute**, **AmazonDynamoDBFullAccess**, **AmazonSNSFullAccess**, **AmazonS3FullAccess** và ấn phím Enter để tìm kiếm policy này.
  + Click chọn policy **AWSLambdaExecute**.
  + Click chọn policy **AmazonDynamoDBFullAccess**.
  + Click chọn policy **AmazonSNSFullAccess**.
  + Click chọn policy **AmazonS3FullAccess**.
  + Click **Next**

![role](/images/2.prerequisite/createrole2.jpg)

6. Click **Next=**.
7. Đặt tên cho Role là **Lambda** ở Role Name  
  + Click **Create Role** \.


Tiếp theo chúng ta sẽ cài đặt và triển khai **Lambda**.