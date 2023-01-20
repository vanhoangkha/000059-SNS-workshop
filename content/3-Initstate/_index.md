---
title : "Using SAM to deploy infrastructure"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 3. </b> "
---

#### Using SAM to deploy infrastructure

1. Access to **Cloud9**


- Select **Your environments**
- Select **WildRydesAsyncMessaging**
- Select **Open IDE**

![Working with SNS](/images/2/2.1/0001.png?featherlight=false&width=90pc)

2. After opening the **Cloud9** interface. We start building artifacts from the source

```
cd ~/environment/wild-rydes-async-messaging/lab-1
sam build
```

![Working with SNS](/images/2/2.1/0002.png?featherlight=false&width=90pc)

3. Next we deploy the application

```
export AWS_REGION=$(aws --profile default configure get region)
sam deploy \
    --stack-name wild-rydes-async-msg-1 \
    --capabilities CAPABILITY_IAM \
    --region $AWS_REGION \
    --guided
```

- Type **Enter** 4 times
- Go to **SubmitRideCompletionFunction may not have authorization defined, Is this okay? [y/N]:** then enter **```y```**
- Continue typing **Enter** 4 more times.

![Working with SNS](/images/2/2.1/0003.png?featherlight=false&width=90pc)

4. Wait for 10 minutes to complete the application deployment.

![Working with SNS](/images/2/2.1/0004.png?featherlight=false&width=90pc)

5. Check from the stack interface of **CloudFormation** that the stack has been created.

![Working with SNS](/images/2/2.1/0005.png?featherlight=false&width=90pc)

6. Check the **Lambda** interface, there are already 4 functions created.

![Working with SNS](/images/2/2.1/0006.png?featherlight=false&width=90pc)

7. Check **DynamoDB**, a new table has appeared.

![Working with SNS](/images/2/2.1/0007.png?featherlight=false&width=90pc)