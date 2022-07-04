---
title : "Tạo Customer accounting service"
date :  "`r Sys.Date()`" 
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

#### Tạo Customer accounting service

1. Truy cập vào **SNS**

- Chọn **Topic**
- Chọn **RideCompletionTopic**
- Chọn **Create subscription**

![Working with SNS](/images/2/2.4/0001.png?featherlight=false&width=90pc)

2. Quay lại giao diện **Cloud9** chạy lệnh để xem Endpoint

```
aws cloudformation describe-stacks \
    --stack-name wild-rydes-async-msg-1 \
    --query 'Stacks[].Outputs[?OutputKey==`CustomerAccountingFunction`].OutputValue' \
    --output text
```

![Working with SNS](/images/2/2.4/0002.png?featherlight=false&width=90pc)

3. Trong giao diện **Create subscription**

- **Topic ARN** giữ mặc định
- **Protocol**, chọn **Lambda**
- **Endpoint**, nhập giá trị **Output** của Cloud9
- Chọn **Create subscription**

![Working with SNS](/images/2/2.4/0003.png?featherlight=false&width=90pc)

4. Hoàn thành tạo subscription

![Working with SNS](/images/2/2.4/0004.png?featherlight=false&width=90pc)

5. Truy cập vào **AWS Lambda**

- Chọn **Customer Accounting function**

![Working with SNS](/images/2/2.4/0005.png?featherlight=false&width=90pc)

6. Kiểm tra Lambda function đã trigger SNS.

![Working with SNS](/images/2/2.4/0006.png?featherlight=false&width=90pc)
