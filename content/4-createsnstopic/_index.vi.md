---
title : "Tạo Amazon SNS Topic"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

#### Tạo Amazon SNS Topic

1. Truy cập giao diện **Cloud9 IDE**

- Mở **SAM template** **wild-rydes-async-messaging/lab-1/template.yaml**
- Trong phần **Resources**, bỏ comment đoạn code sau:

```
  RideCompletionTopic:
    Type: AWS::SNS::Topic
    Properties:
      TopicName: RideCompletionTopic
```

![Working with SNS](/images/2/2.2/0002.png?featherlight=false&width=90pc)

2. Thực hiện cập nhật **AWS SAM template**

```
cd ~/environment/wild-rydes-async-messaging/lab-1
sam build
```

![Working with SNS](/images/2/2.2/0003.png?featherlight=false&width=90pc)

3. Thực hiện triển khai khởi tạo **SNS topic**

```
sam deploy
```

![Working with SNS](/images/2/2.2/0004.png?featherlight=false&width=90pc)