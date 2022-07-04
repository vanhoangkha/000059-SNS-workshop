---
title : "Create Customer accounting service"
date : "`r Sys.Date()`"
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

#### Create Customer accounting service

1. Access to **SNS**

- Select **Topic**
- Select **RideCompletionTopic**
- Select **Create subscription**

![Working with SNS](/images/2/2.4/0001.png?featherlight=false&width=90pc)

2. Go back to the **Cloud9** interface and run the command to see the Endpoint

```
aws cloudformation describe-stacks \
    --stack-name wild-rydes-async-msg-1 \
    --query 'Stacks[].Outputs[?OutputKey==`CustomerAccountingFunction`].OutputValue' \
    --output text
```

![Working with SNS](/images/2/2.4/0002.png?featherlight=false&width=90pc)

3. In the **Create subscription** interface

- **Topic ARN** keep default
- **Protocol**, select **Lambda**
- **Endpoint**, enter the value **Output** of Cloud9
- Select **Create subscription**

![Working with SNS](/images/2/2.4/0003.png?featherlight=false&width=90pc)

4. Complete subscription creation

![Working with SNS](/images/2/2.4/0004.png?featherlight=false&width=90pc)

5. Access to **AWS Lambda**

- Select **Customer Accounting function**

![Working with SNS](/images/2/2.4/0005.png?featherlight=false&width=90pc)

6. Check the Lambda function that triggered the SNS.

![Working with SNS](/images/2/2.4/0006.png?featherlight=false&width=90pc)