---
title : "Kiểm tra Fan-Out và lọc tin nhắn"
date :  "`r Sys.Date()`" 
weight : 9
chapter : false
pre : " <b> 9. </b> "
---

#### Kiểm tra Fan-Out và lọc tin nhắn

Trong bước này, chúng tôi sẽ xác nhận rằng Amazon SNS Topic đang xuất bản tất cả các tin nhắn cho tất cả người đăng ký. Vì người đăng ký cũng có thể không xử lý được tin nhắn, chúng tôi cũng muốn xác nhận rằng Amazon SNS đang gửi lại tin nhắn để chúng tôi không bỏ lỡ một tin nhắn nào.

1. Kiểm tra **API Gateway endpoint**

```
aws cloudformation describe-stacks \
    --stack-name wild-rydes-async-msg-1 \
    --query 'Stacks[].Outputs[?OutputKey==`UnicornManagementServiceApiSubmitRideCompletionEndpoint`].OutputValue' \
    --output text
```

![Working with SNS](/images/2/2.7/0001.png?featherlight=false&width=90pc)

2.  Lưu trữ API Gateway endpoint URL.
```
export ENDPOINT=$(aws cloudformation describe-stacks \
    --stack-name wild-rydes-async-msg-1 \
    --query 'Stacks[].Outputs[?OutputKey==`UnicornManagementServiceApiSubmitRideCompletionEndpoint`].OutputValue' \
    --output text)
```

- Gửi couple request đến **Unicorn Management Service**

```
curl -XPOST -i -H "Content-Type:application/json" -d '{ "from": "Berlin", "to": "Frankfurt", "duration": 420, "distance": 600, "customer": "cmr", "fare": 256.50 }' $ENDPOINT
```

![Working with SNS](/images/2/2.7/0002.png?featherlight=false&width=90pc)

3. Truy cập vào **CloudWatch**

- Chọn **Log groups**
- Chọn **/aws/lambda/wild-rydes-async-msg-1-**

![Working with SNS](/images/2/2.7/0003.png?featherlight=false&width=90pc)

4. Trong giao diện log group

- Chọn **Log streams**
- Chọn log stream đã được tạo.

![Working with SNS](/images/2/2.7/0004.png?featherlight=false&width=90pc)

5. Quan sát chi tiết log events.

![Working with SNS](/images/2/2.7/0005.png?featherlight=false&width=90pc)