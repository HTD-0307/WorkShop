---
title : "Tạo Cảm biến giả lập"
date : 2023-10-25 
weight : 3
chapter : false
pre : " <b> 2.1.3 </b> "
---

#### Tạo Cảm biến giả lập

1. Tải [Python](https://www.python.org/downloads/)
  + Cài đặt file .exe  vừa tải về.
  + Vào **terminal** nhập dòng lệnh: **python --verion**

![VPC](/images/2.prerequisite/createpython.jpg)

2. Tải [AWS Command Line Interface](https://aws.amazon.com/vi/cli/)
  + Chạy file cài đặt .msi
  + Kiểm tra bằng lệnh: **aws --version**

![VPC](/images/2.prerequisite/createCLI.jpg)


3. Cấu Hình Tài Khoản AWS
  + Vào AWS Management Console, vào dịch vụ IAM
  + Click **My security credentials**
  ![VPC](/images/2.prerequisite/createIAM.jpg)
  ![VPC](/images/2.prerequisite/createIAM1.jpg)
  + Khi trang **My security credentials** xuất hiện, click **Create access key**.
  + Khi trang **Create access key** xuất hiện:
    + Click vào ô chọn **I understand creating a root access key is not a best practice, but I still want to create one**
    + Click **Create access key**.
    + Download file .csv về máy.
![VPC](/images/2.prerequisite/createIAM3.jpg)
![VPC](/images/2.prerequisite/createIAM4.jpg)
  + Mở terminal, chạy lệnh **aws configure**:
      + Nhập Access Key, Secret Key từ file .csv vừa tải
      + Region: us-east-1
      + Output format: json
![VPC](/images/2.prerequisite/createIAM5.jpg)

4. Cài Đặt Thư Viện **boto3**
  + Mở terminal, cài đặt thư viện **boto3** bằng lệnh: **pip install boto3**
![VPC](/images/2.prerequisite/createIAM6.jpg)
5. Tạo file spr
