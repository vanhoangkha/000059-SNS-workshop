---
title : "Create Customer notification service"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

#### Create Customer notification

1. Access to **AWS SNS**

- Select **RideCompletionTopic**
- Select **Create subscription**

![Working with SNS](/images/2/2.3/0001.png?featherlight=false&width=90pc)

2. Return to **Cloud9** interface to run the command to view Endpoint

```
aws cloudformation describe-stacks \
    --stack-name wild-rydes-async-msg-1 \
    --query 'Stacks[].Outputs[?OutputKey==`CustomerNotificationFunction`].OutputValue' \
    --output text
```

![Working with SNS](/images/2/2.3/0002.png?featherlight=false&width=90pc)

3. In the **Create subscription** interface

- **Topic ARN** to default
- **Protocol** select **AWS Lambda**
- **Enpoint**, import the output from Cloud9
- Select **Create subscription**

![Working with SNS](/images/2/2.3/0003.png?featherlight=false&width=90pc)

4. Access to **Lambda**

- Select **Customer Notification function**

![Working with SNS](/images/2/2.3/0004.png?featherlight=false&width=90pc)

5. Check the Lambda function that triggered the SNS.

![Working with SNS](/images/2/2.3/0005.png?featherlight=false&width=90pc)