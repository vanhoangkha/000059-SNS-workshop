---
title : "Create Amazon SNS Topic"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

#### Create Amazon SNS Topic

1. Access the **Cloud9 IDE** interface

- Open **SAM template** **wild-rydes-async-messaging/lab-1/template.yaml**
- In the **Resources** section, uncomment the following code:

```
  RideCompletionTopic:
    Type: AWS::SNS::Topic
    Properties:
      TopicName: RideCompletionTopic
```

![Working with SNS](/images/2/2.2/0002.png?featherlight=false&width=90pc)

2. Update **AWS SAM template**

```
cd ~/environment/wild-rydes-async-messaging/lab-1
Sam build
```

![Working with SNS](/images/2/2.2/0003.png?featherlight=false&width=90pc)

3. Implement initialization **SNS topic**

```
sam deploy
```

![Working with SNS](/images/2/2.2/0004.png?featherlight=false&width=90pc)