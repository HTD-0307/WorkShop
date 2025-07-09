---
title : "Cấu hình AWS IoT Core"
date : 2023-10-25 
weight : 4 
chapter : false
pre : " <b> 4. </b> "
---


Để có thể nhận được dữ liệu từ nguồn cảm biến tự động, chúng ta cần phải cài đặt cấu hình cho AWS IoT Core.
Truy cập vào [giao diện quản trị của dịch vụ AWS IoT Core](https://console.aws.amazon.com/iot/home).

1. Tạo **Thing**
  + Chọn **Thing**
  + Click vào **Create thing**


![S3](/images/4.s3/createIoT.jpg)

  + Tại mục **Number of thing to create**
    + Chọn Create single thing
    + Chọn **Next**

![S3](/images/4.s3/createIoT1.jpg)

  + Khi mục **Specify thing properties** xuất hiện
    + Tại mục **Thing name**  điền **InventorySensor**
    + Chọn **Next**

![S3](/images/4.s3/createIoT2.jpg)

  + Tại mục **Device certificate** chọn **Auto-generate a new certificate**
  + Chọn **Next**

![S3](/images/4.s3/createIoT3.jpg)

  + Chọn create thing
  + Downloal các file trong bảng **Downloal certificates and key** về máy

![S3](/images/4.s3/createIoT4.jpg)

2. Tạo các chính sách
  + Tại mục **Security**, chọn **Policies**
  + Chọn **Create policy**
![S3](/images/4.s3/createIoT5.jpg)

  + Tại **Policy name** điền **IoTInventoryPolicy**
  + Tại **Policy action**:
    + Chọn **iot:Connect**
    + Chọn **iot:Publish**
    + Chọn **iot:Subscribe**
    + Chọn **iot:Receive**
  + Tại **Policy resource** điền **arn:aws:sns:us-east-1:922456364996:InventoryAlerts**
![S3](/images/4.s3/createIoT7.jpg)

  + Chọn mục **Certificates**
    + Click chọn **Certificates** của dự án
    + Chọn **Action** và chọn **Attach policy**

![S3](/images/4.s3/createIoT6.jpg)

  + Tại **Policies** chọn **IoTInventoryPolicy**
  + Chọn**Attach policies**

![S3](/images/4.s3/createIoT8.jpg)

  + Tiếp tục chọn **Attach to things**

![S3](/images/4.s3/createIoT9.jpg)

  + Tại **Things** chọn **InventorySensor1**
  + Chọn **Attach to thing**

![S3](/images/4.s3/createIoT10.jpg)

3. Tạo rule

  + Chọn **Message routing**
    + Chọn **Rule**
    + Chọn **Create rule**

![S3](/images/4.s3/createIoT11.jpg)

  + Tại **Rule name**điền **InventoryRule**
  + Chọn **Next**

![S3](/images/4.s3/createIoT12.jpg)

  + Tại **SQL statement** điền **SELECT * FROM 'inventory/sensor1/data'**
  + Chọn **Next**

![S3](/images/4.s3/createIoT14.jpg)

  + Tại **Action1** chọn **Lambda**
  + Tại **Lambda function** chọn **ProcessInventoryData**
  + Tại **Lambda function version** chọn **$LATEST**
  + Chọn **Next**

![S3](/images/4.s3/createIoT15.jpg)

+ Chọn **Create**

![S3](/images/4.s3/createIoT13.jpg)