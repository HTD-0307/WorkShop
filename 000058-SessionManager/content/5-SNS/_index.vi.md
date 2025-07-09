---
title : "Tạo SNS"
date : 2023-10-25 
weight : 5 
chapter : false
pre : " <b> 5. </b> "
---

#### Tạo SNS
1. Truy cập [giao diện quản trị dịch vụ SNS](https://console.aws.amazon.com/sns/home)
  + Click **Topic**.
  + Click **Create topic**.

![VPC](/images/5.SNS/createSNS1.jpg)
![VPC](/images/5.SNS/createSNS2.jpg)

2. Tại trang **Create Topic**.
  + Tại mục **Type** chọn **Standard**.
  + Tại mục **Name** điền : **InventoryAlerts**.
  + Click **Create Topic**.

![VPC](/images/5.SNS/createSNS3.jpg)
![VPC](/images/5.SNS/createSNS4.jpg)

3. Tạo **Subscriptions**
  + Click **Subscriptions**
  + Chọn **Create Subscriptions**
![VPC](/images/5.SNS/createSNS7.jpg)

  + Khi xuất hiện mục **Create Subscriptions**
    + Tại **Topic ARN** chọn **arn:aws:sns:us-east-1:922456364996:InventoryAlerts:f2b3d4d3-794d-42f4-a76e-5974a6514506**
    + tại **Protocol** chọn **Email**
    + Tại **Endpoint** nhập Email nhận cảnh báo.
  + Chọn **Create Subscriptions**

![VPC](/images/5.SNS/createSNS5.jpg)

  + Vào email đăng ký SNS kiểm tra để kích hoạt.
![VPC](/images/5.SNS/createSNS6.jpg)