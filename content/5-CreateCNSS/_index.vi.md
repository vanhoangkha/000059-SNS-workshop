---
title : "Tạo Customer notification service"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

#### Tạo Customer notification

1. Truy cập vào **AWS SNS**

- Chọn **RideCompletionTopic**
- Chọn **Create subscription**

![Working with SNS](/images/2/2.3/0001.png?featherlight=false&width=90pc)

2. Quay lại giao diện **Cloud9** để chạy lệnh xem Enpoint

```
aws cloudformation describe-stacks \
    --stack-name wild-rydes-async-msg-1 \
    --query 'Stacks[].Outputs[?OutputKey==`CustomerNotificationFunction`].OutputValue' \
    --output text
```

![Working with SNS](/images/2/2.3/0002.png?featherlight=false&width=90pc)

3. Trong giao diện **Create subscription**

- **Topic ARN** để mặc định
- **Protocol** chọn **AWS Lambda**
- **Enpoint**, nhập kết quả output từ Cloud9
- Chọn **Create subscription**

![Working with SNS](/images/2/2.3/0003.png?featherlight=false&width=90pc)

4. Truy cập vào **Lambda**

- Chọn **Customer Notification function**

![Working with SNS](/images/2/2.3/0004.png?featherlight=false&width=90pc)

5. Kiểm tra Lambda function đã trigger SNS.

![Working with SNS](/images/2/2.3/0005.png?featherlight=false&width=90pc)




