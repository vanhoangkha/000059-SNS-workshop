---
title : "Sử dụng SAM triển khai hạ tầng"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 3. </b> "
---

#### Sử dụng SAM triển khai hạ tầng

1. Truy cập vào **Cloud9**


- Chọn **Your environments**
- Chọn **WildRydesAsyncMessaging**
- Chọn **Open IDE**

![Working with SNS](/images/2/2.1/0001.png?featherlight=false&width=90pc)

2. Sau khi mở giao diện **Cloud9**. Chúng ta bắt đầu build artifacts từ source

```
cd ~/environment/wild-rydes-async-messaging/lab-1
sam build
```

![Working with SNS](/images/2/2.1/0002.png?featherlight=false&width=90pc)

3. Tiếp theo chúng ta triển khai ứng dụng

```
export AWS_REGION=$(aws --profile default configure get region)
sam deploy \
    --stack-name wild-rydes-async-msg-1 \
    --capabilities CAPABILITY_IAM \
    --region $AWS_REGION \
    --guided
```

- Gõ **Enter** 4 lần
- Đến phần **SubmitRideCompletionFunction may not have authorization defined, Is this okay? [y/N]:** thì nhập **```y```**
- Tiếp tục gõ **Enter** 4 lần nữa.

![Working with SNS](/images/2/2.1/0003.png?featherlight=false&width=90pc)

4. Đợi khoảnh 10 phút sau, hoàn thành triển khai ứng dụng.

![Working with SNS](/images/2/2.1/0004.png?featherlight=false&width=90pc)

5. Kiểm tra từ giao diện stack của **CloudFormation** thì stack đã được tạo.

![Working with SNS](/images/2/2.1/0005.png?featherlight=false&width=90pc)

6. Kiểm tra giao diện **Lambda** thì đã có 4 hàm được tạo.

![Working with SNS](/images/2/2.1/0006.png?featherlight=false&width=90pc)

7. Kiểm tra **DynamoDB** thì đã có 1 bảng mới xuất hiện.

![Working with SNS](/images/2/2.1/0007.png?featherlight=false&width=90pc)

