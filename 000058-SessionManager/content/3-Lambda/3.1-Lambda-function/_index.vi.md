---
title : "Tạo Lambda function"
date : 2023-10-25 
weight : 1 
chapter : false
pre : " <b> 3.1. </b> "
---

1. Truy cập vào [giao diện quản trị của dịch vụ Lambda](https://console.aws.amazon.com/lambda/home).
  + Click chọn **Create Function**.

![Connect](/images/3.connect/createlambda.jpg)

2. Tại trang Create function.
  + Click chọn **Author from scratch**.
  + Tại mục **Function name** điền **ProcessInventoryData**.
  + Tại mục **runtime** chọn **python 3.9**.
  + Tại mục **Execution role** chọn **Use an existing role**
  + Tại mục **Existing role** chọn role đã tạo ở IAM lúc trước.

![Connect](/images/3.connect/createlambda1.jpg)

3. Kéo xuống cuối trang chọn **Create function**
![Connect](/images/3.connect/createlambda2.jpg)