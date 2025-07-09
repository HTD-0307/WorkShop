---
title : "Viết code xử lý cho Lambda"
date : 2023-10-25 
weight : 2 
chapter : false
pre : " <b> 3.2. </b> "
---
Để Lambda có thể xử lý dữ liệu nhận được từu IoT Core, chúng ta cần viết 1 hàm xử lý các tác vụ:lưu dữ liệu vào DynamoDB, gửi cảnh báo khi dữ lieuj vượt ngưỡng.

1. Truy cập vào [giao diện quản trị của dịch vụ Lambda](https://console.aws.amazon.com/lambda/home).
  + Click chọn **Function**.
  + Click chọn function vừa tạo
![Connect](/images/3.connect/createlambda4.jpg) 

2. Khi mục **ProcessInventoryData** xuất hiện
   + Chọn mục **Code**
   + Dán đoạn code này:
```python
import boto3
import json

dynamodb = boto3.resource('dynamodb')
table = dynamodb.Table('InventoryData')
sns = boto3.client('sns')

def lambda_handler(event, context):
    print("Received event:", event)
    # Xử lý batch format từ IoT rule
    if 'records' in event:
        for record in event['records']:
            try:
                payload = json.loads(record['data'])
                print("Processing payload (batch):", payload)
                process_data(payload)
            except Exception as e:
                print("Error processing batch record:", str(e))
    # Xử lý single event (ví dụ từ script hoặc test)
    elif all(key in event for key in ['product_id', 'quantity', 'timestamp']):
        print("Processing single event:", event)
        process_data(event)
    else:
        print("Invalid event format, skipping")
    return {'statusCode': 200}

def process_data(payload):
    product_id = payload['product_id']
    quantity = payload['quantity']
    timestamp = payload['timestamp']

    table.put_item(Item=payload)
    print("Saved to DynamoDB:", payload)

    if quantity < 10:
        sns.publish(
            TopicArn='arn:aws:sns:us-east-1:922456364996:InventoryAlerts',
            Message=f"Low inventory for {product_id}: {quantity} units"
        )
        print("Sent SNS alert")
```
   + Click **Deploy** để update cho **Lambda**
![Connect](/images/3.connect/createlambda3.jpg) 