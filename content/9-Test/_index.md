---
title : "Test Fan-Out and message filtering"
date : "`r Sys.Date()`"
weight : 9
chapter : false
pre : " <b> 9. </b> "
---

#### Test Fan-Out and filter messages

In this step, we will confirm that Amazon SNS Topic is publishing all messages to all subscribers. Since the subscriber may also not be able to process the message, we also want to confirm that Amazon SNS is resending the message so that we don't miss a single message.

1. Check **API Gateway endpoint**

```
aws cloudformation describe-stacks \
    --stack-name wild-rydes-async-msg-1 \
    --query 'Stacks[].Outputs[?OutputKey==`UnicornManagementServiceApiSubmitRideCompletionEndpoint`].OutputValue' \
    --output text
```

![Working with SNS](/images/2/2.7/0001.png?featherlight=false&width=90pc)

2. Store the API Gateway endpoint URL.
```
export ENDPOINT=$(aws cloudformation describe-stacks \
    --stack-name wild-rydes-async-msg-1 \
    --query 'Stacks[].Outputs[?OutputKey==`UnicornManagementServiceApiSubmitRideCompletionEndpoint`].OutputValue' \
    --output text)
```

- Send couple request to **Unicorn Management Service**

```
curl -XPOST -i -H "Content-Type:application/json" -d '{ "from": "Berlin", "to": "Frankfurt", "duration": 420, "distance": 600, "customer ": "cmr", "fare": 256.50 }' $ENDPOINT
```

![Working with SNS](/images/2/2.7/0002.png?featherlight=false&width=90pc)

3. Access to **CloudWatch**

- Select **Log groups**
- Select **/aws/lambda/wild-rydes-async-msg-1-**

![Working with SNS](/images/2/2.7/0003.png?featherlight=false&width=90pc)

4. In the log group interface

- Select **Log streams**
- Select the log stream that has been created.

![Working with SNS](/images/2/2.7/0004.png?featherlight=false&width=90pc)

5. Observe detailed log events.

![Working with SNS](/images/2/2.7/0005.png?featherlight=false&width=90pc)