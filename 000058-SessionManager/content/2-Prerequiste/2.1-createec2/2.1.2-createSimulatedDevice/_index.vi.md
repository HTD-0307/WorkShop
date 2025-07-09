---
title : "Tạo Cảm biến giả lập"
date : 2023-10-25 
weight : 2
chapter : false
pre : " <b> 2.1.2 </b> "
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
5. Tạo file **sensor_simulator.py** trên thiết bị giả lập
  + Sao chép đoạn code dưới vào file py vừa tạo:
```python
import paho.mqtt.client as mqtt
import json
import time
import random
from datetime import datetime, timezone

# Cấu hình AWS IoT Core
iot_endpoint = "a2tzdij2wt8lg0-ats.iot.us-east-1.amazonaws.com"
port = 8883
topic = "inventory/sensor1/data"
cert_file = "C:/Users/HUYNHDO/Desktop/ThucTap/WorkShop/IoT/7fa53e8ed2f2f2f0937741775116a7061656dc2ff0b7b66c33085435a223a63e-certificate.pem.crt"
key_file = "C:/Users/HUYNHDO/Desktop/ThucTap/WorkShop/IoT/7fa53e8ed2f2f2f0937741775116a7061656dc2ff0b7b66c33085435a223a63e-private.pem.key"
ca_file = "C:/Users/HUYNHDO/Desktop/ThucTap/WorkShop/IoT/AmazonRootCA1.pem"

def on_connect(client, userdata, flags, rc, properties=None):
    """Callback khi kết nối với broker MQTT."""
    if rc == 0:
        print("Kết nối thành công với AWS IoT Core")
        client.subscribe(topic, qos=1)
    else:
        print(f"Kết nối thất bại với mã lỗi {rc}")

def on_publish(client, userdata, mid):
    """Callback khi tin nhắn được gửi thành công."""
    print(f"Tin nhắn {mid} được gửi thành công")

def on_disconnect(client, userdata, rc):
    """Callback khi mất kết nối."""
    print(f"Mất kết nối với mã lỗi {rc}")

def generate_inventory_data():
    """Tạo dữ liệu mẫu cho hàng tồn kho."""
    return {
        "product_id": f"PROD-{random.randint(1, 100)}",
        "quantity": random.randint(0, 30),  # Tạo số lượng thấp để kiểm tra cảnh báo
        "warehouse_id": "WH1",
        "timestamp": datetime.now(timezone.utc).isoformat()
    }

# Khởi tạo client MQTT
client = mqtt.Client(client_id="SensorSimulator", protocol=mqtt.MQTTv5)
client.tls_set(ca_file, cert_file, key_file)
client.on_connect = on_connect
client.on_publish = on_publish
client.on_disconnect = on_disconnect

# Kết nối đến AWS IoT Core
try:
    client.connect(iot_endpoint, port, keepalive=120)  # Tăng keepalive để ổn định kết nối
except Exception as e:
    print(f"Kết nối thất bại: {e}")
    exit(1)

# Bắt đầu vòng lặp để xử lý kết nối và tin nhắn
client.loop_start()

# Vòng lặp xuất bản dữ liệu
try:
    while True:
        data = generate_inventory_data()
        payload = json.dumps(data)
        result = client.publish(topic, payload, qos=1)
        if result.rc == mqtt.MQTT_ERR_SUCCESS:
            print(f"Published: {payload}")
        else:
            print(f"Failed to publish: {result.rc}")
        time.sleep(60)  # Gửi dữ liệu mỗi 60 giây
except KeyboardInterrupt:
    print("Dừng script")
    client.loop_stop()
    client.disconnect()
```
 + Thay đường dẫn đến các file
    + **cert_file**
    + **key_file**
    + **ca_file**
  đến các file tải về sau khi tạo AWS IoT Core