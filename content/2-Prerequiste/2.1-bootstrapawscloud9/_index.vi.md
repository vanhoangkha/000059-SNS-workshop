---
title : "Triển khai hạ tầng"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 2.1 </b> "
---

#### Triển khai hạ tầng

1. Trước hết để thực hiện bài lab, chúng ta cần khởi tạo tài nguyên bằng **CloudFormation**

- Các bạn truy cập vào đường dẫn để khởi tạo tài nguyên [Serverless](https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/create/review?stackName=wild-rydes-async-msg-0&templateURL=https://s3.amazonaws.com/ee-assets-prod-us-east-1%2fmodules%2f32af13c099e8423b8edb09255cec1b9f%2fv4%2ftemplate.yaml)
- Kiểm tra lại giao diện và chọn **Create stack**

![Working with SNS](/images/1/0001.png?featherlight=false&width=90pc)

2. Đợi khoảng 5-10 phút sau, Stack sẽ khởi tạo thành công  

![Working with SNS](/images/1/0002.png?featherlight=false&width=90pc)

3. Chọn **Ouput** của stack vừa tạo. Sau đó truy cập vào đường dẫn **Cloud9** đã tạo.

![Working with SNS](/images/1/0003.png?featherlight=false&width=90pc)

4. Thực hiện cấu hình môi trường **Cloud9** đã tạo từ **CloudFormation stack**

```
cd ~/environment/wild-rydes-async-messaging/code/lab-0
chmod +x configureCloud9.sh
./configureCloud9.sh
```

![Working with SNS](/images/1/0004.png?featherlight=false&width=90pc)

