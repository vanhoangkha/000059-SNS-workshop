---
title : "Deploy infrastructure"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 2.1 </b> "
---

#### Deploy infrastructure

1. First of all to do the lab, we need to initialize the resource with **CloudFormation**

- You access the link to initialize the resource [Serverless](https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/create/review?stackName=wild-rydes-async-msg-0&templateURL=https://s3.amazonaws.com/ee-assets-prod-us-east-1%2fmodules%2f32af13c099e8423b8edb09255cec1b9f%2fv4%2ftemplate.yaml)
- Check the interface and select **Create stack**

![Working with SNS](/images/1/0001.png?featherlight=false&width=90pc)

2. Wait about 5-10 minutes, Stack will initialize successfully

![Working with SNS](/images/1/0002.png?featherlight=false&width=90pc)

3. Select **Output** of the stack just created. Then access the path **Cloud9** created.

![Working with SNS](/images/1/0003.png?featherlight=false&width=90pc)

4. Configure the **Cloud9** environment created from the **CloudFormation stack**

```
cd ~/environment/wild-rydes-async-messaging/code/lab-0
chmod +x configureCloud9.sh
./configureCloud9.sh
```

![Working with SNS](/images/1/0004.png?featherlight=false&width=90pc)