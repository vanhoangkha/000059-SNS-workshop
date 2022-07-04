---
title : "Tạo Extraordinary rides service"
date :  "`r Sys.Date()`" 
weight : 7
chapter : false
pre : " <b> 7. </b> "
---

#### Tạo Extraordinary rides service

Sau khi đã tạo SNS subscription bằng console, chúng ta sẽ thử tạo subscription SNS bằng SAM.

1. Cập nhật **AWS SAM template**

- Mở file **wild-rydes-async-messaging/lab-1/template.yaml** trong **Cloud9** và cập nhật đoạn code sau

```
Events:
  SNSEvent:
    Type: SNS
    Properties:
      Topic: !Ref RideCompletionTopic
      FilterPolicy:
        fare:
          - numeric:
              - '>='
              - 50
        distance:
          - numeric:
              - '>='
              - 20
```

![Working with SNS](/images/2/2.5/0001.png?featherlight=false&width=90pc)

2. Cập nhật bằng lệnh sau:

```
cd ~/environment/wild-rydes-async-messaging/lab-1
sam build
```

![Working with SNS](/images/2/2.5/0002.png?featherlight=false&width=90pc)

3. Sau khi cập nhật chúng ta sẽ triển khai bằng lệnh:

```
sam deploy
```

![Working with SNS](/images/2/2.5/0003.png?featherlight=false&width=90pc)

4. Kiểm tra subscription đã tạo thành công.

![Working with SNS](/images/2/2.5/0004.png?featherlight=false&width=90pc)

5. Kiểm tra Lambda Function đã trigger SNS.

![Working with SNS](/images/2/2.5/0005.png?featherlight=false&width=90pc)

