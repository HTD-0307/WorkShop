---
title : "Chuẩn bị"
date : 2023-10-25 
weight : 1 
chapter : false
pre : " <b> 2.1 </b> "
---

Trong bước này, chúng ta sẽ cần tạo một VPC có 2 subnet public / private. Sau đó tạo 1 EC2 Instance Linux nằm trong public subnet,  1 EC2 Instance Windows nằm trong private subnet.

Tổng quan kiến trúc sau khi các bạn hoàn tất bước này sẽ như sau:

![VPC](/images/sodo.jpg)

Để tìm hiểu cách tạo các EC2 instance và VPC với public/private subnet các bạn có thể tham khảo bài lab :
  - [Giới thiệu về Amazon EC2](https://000004.awsstudygroup.com/vi/)
  - [Làm việc với Amazon VPC](https://000003.awsstudygroup.com/vi/) 


### Nội dung
  - [Tạo SNS](2.1.1-createsns/)
  - [Tạo DynamoDB](2.1.2-createdynamodb/)
  - [Tạo Giả lập cảm biến](2.1.3-createSimulatedDevice/)