---
title: "Write Processing Code for Lambda"  
date: 2023-10-25  
weight: 2  
chapter: false  
pre: " <b> 3.2. </b> "  
---  
To enable Lambda to process data received from IoT Core, we need to write a function to handle tasks: storing data in DynamoDB and sending alerts when the data exceeds thresholds.  

1. Access the [Lambda service management interface](https://console.aws.amazon.com/lambda/home).  
 + Click on **Function**.  
 + Click on the function you just created.  
![Connect](/images/3.connect/createlambda4.jpg)  

2. When the **ProcessInventoryData** section appears,  
 + Select the **Code** section.  
 + Paste this code:  
```python
import json
import boto3
import time
from decimal import Decimal

# Khởi tạo các client AWS
dynamodb = boto3.resource('dynamodb')
s3 = boto3.client('s3')
sns = boto3.client('sns')

# Cấu hình
TABLE_NAME = 'Inventory'
BUCKET_NAME = 'iot-log-2025'
SNS_TOPIC_ARN = 'arn:aws:sns:us-east-1:922456364996:InventoryAlerts'  # Thay bằng ARN của SNS Topic
QUANTITY_THRESHOLD = 20

def lambda_handler(event, context):
    print(f"Received event: {json.dumps(event)}")
    try:
        # Lấy dữ liệu từ IoT Core
        product_id = event['product_id']
        quantity = event['quantity']
        warehouse_id = event['warehouse_id']
        timestamp = event['timestamp']
        print(f"Processing: product_id={product_id}, quantity={quantity}")
        
        # Lưu dữ liệu vào DynamoDB
        table = dynamodb.Table(TABLE_NAME)
        table.put_item(
            Item={
                'product_id': product_id,
                'timestamp': timestamp,
                'quantity': Decimal(str(quantity)),
                'warehouse_id': warehouse_id
            }
        )
        print(f"Successfully saved to DynamoDB")
        
        # Tạo báo cáo JSON và tải lên S3
        report = {
            'product_id': product_id,
            'quantity': quantity,
            'warehouse_id': warehouse_id,
            'timestamp': timestamp,
            'status': 'Low' if quantity < QUANTITY_THRESHOLD else 'Normal'
        }
        s3_key = f'reports/{product_id}_{timestamp}.json'
        s3.put_object(
            Bucket=BUCKET_NAME,
            Key=s3_key,
            Body=json.dumps(report)
        )
        print(f"Successfully uploaded to S3: {s3_key}")
        
        # Gửi cảnh báo qua SNS nếu số lượng thấp
        if quantity < QUANTITY_THRESHOLD:
            message = f"Cảnh báo: Sản phẩm {product_id} tại kho {warehouse_id} có số lượng thấp ({quantity}) vào thời điểm {timestamp}."
            sns.publish(
                TopicArn=SNS_TOPIC_ARN,
                Message=message,
                Subject='Cảnh báo Hàng tồn kho Thấp'
            )
            print(f"Sent SNS alert for low inventory")
        
        return {
            'statusCode': 200,
            'body': json.dumps('Xử lý dữ liệu thành công')
        }
    
    except Exception as e:
        print(f"Lỗi: {str(e)}")
        return {
            'statusCode': 500,
            'body': json.dumps(f"Lỗi: {str(e)}")
        }
```
+ Click **Deploy** to update **Lambda**
![Connect](/images/3.connect/createlambda3.jpg)