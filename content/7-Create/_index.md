---
title : "Create Extraordinary rides service"
date : "`r Sys.Date()`"
weight : 7
chapter : false
pre : " <b> 7. </b> "
---

#### Create Extraordinary rides service

After we have created an SNS subscription using the console, we will try to create an SNS subscription using SAM.

1. Update **AWS SAM template**

- Open the file **wild-rydes-async-messaging/lab-1/template.yaml** in **Cloud9** and update the following code

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

2. Update with the following command:

```
cd ~/environment/wild-rydes-async-messaging/lab-1
Sam build
```

![Working with SNS](/images/2/2.5/0002.png?featherlight=false&width=90pc)

3. After updating we will deploy with the command:

```
sam deploy
```

![Working with SNS](/images/2/2.5/0003.png?featherlight=false&width=90pc)

4. Check the subscription has been created successfully.

![Working with SNS](/images/2/2.5/0004.png?featherlight=false&width=90pc)

5. Check Lambda Function triggered SNS.

![Working with SNS](/images/2/2.5/0005.png?featherlight=false&width=90pc)