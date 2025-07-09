---
title : "Kết quả thực nghiệm"
date : 2023-10-25 
weight : 7 
chapter : false
pre : " <b> 7. </b> "
---

1. Chạy cảm biến giả lập
    + Vào **Terminal** dẩn đến thu mục file **sensor_simulator.py**
    + Chạy dòng lệnh: **python sensor_simulator.py**
![Demo](/images/7.Demo/demo1.jpg)

2. Vào AWS IoT kiểm tra dữ liệu
    + Truy cập [giao diện quản trị dịch vụ AWS IoT Core](https://console.aws.amazon.com/iot/home)
        + Chọn **MQTT test client**
        + Tại **Topic filter** điền **inventory/sensor1/data**
        + Chọn **Subscribe**
        + Chọn **Publish**
    + Kéo xuống ta có thể thấy được dữ liệu nhận được từ thiết bị cảm biến gửi đến IoT Core.

![Demo](/images/7.Demo/demo2.jpg)
![Demo](/images/7.Demo/demo6.jpg)

3. Kiểm tra log trong CloudWatch
    + Truy cập [giao diện quản trị dịch vụ Cloudwatch](https://console.aws.amazon.com/cloudwatch/home)
        + Chọn **Log groups**
        + Chọn **/aws/lambda/ProcessInventoryData**
        + Tại **Log Stream**, chọn Log stream cập nhật mới nhất
![Demo](/images/7.Demo/demo3.jpg)
![Demo](/images/7.Demo/demo5.jpg)

4. Kiểm tra dữ liệu trong DynamoDB
    + Truy cập [giao diện quản trị dịch vụ DynamoDB](https://console.aws.amazon.com/dynamodb/home)
        + Chọn **Explore items**
        + Chọn table **Inventory**
        + Click **Run**, trong bảng **Table: Inventory - Items returned** sẽ chứa đầy đủ dữ liệu từ cảm biến gửi đến.

![Demo](/images/7.Demo/demo4.jpg)

5. Kiểm tra gmail

    + Mở gmail đã đăng ký dịch vụ SNS

![Demo](/images/7.Demo/demo7.jpg)

    SNS sẽ gửi cảnh báo về mail khi nhận được sản phẩm có số lượng thấp hơn 20.