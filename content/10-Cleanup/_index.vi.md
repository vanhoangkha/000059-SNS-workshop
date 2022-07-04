---
title : "Dọn dẹp tài nguyên"
date :  "`r Sys.Date()`" 
weight : 10
chapter : false
pre : " <b> 10. </b> "
---

#### Dọn dẹp tài nguyên 

#### Xóa  AWS SAM template

1. Vào giao diện AWS Cloud9
2. Chạy lệnh sau:

```
cd ~/environment/wild-rydes-async-messaging/lab-1
aws cloudformation delete-stack \
    --stack-name wild-rydes-async-msg-1
```