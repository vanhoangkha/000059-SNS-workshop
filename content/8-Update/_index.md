---
title : "Update Unicorn Management Service"
date : "`r Sys.Date()`"
weight : 8
chapter : false
pre : " <b> 8. </b> "
---

#### Update Unicorn Management Service

After creating SNS Topic and subscriptions according to the architecture:


![Working with SNS](/images/1/0000.png?featherlight=false&width=90pc)

1. First we grant IAM permission to Lambda

- Updated SAM template **wild-rydes-async-messaging/lab-1/template.yaml**

```
- SNSPublishMessagePolicy:
    TopicName: !GetAtt RideCompletionTopic.TopicName
```

![Working with SNS](/images/2/2.6/0001.png?featherlight=false&width=90pc)

2. Next we have to give **Amazon SNS topic ARN** to Lambda.

- Keep updating SAM template **wild-rydes-async-messaging/lab-1/template.yaml**

```
TOPIC_ARN: !Ref RideCompletionTopic
```

![Working with SNS](/images/2/2.6/0002.png?featherlight=false&width=90pc)

3. Then we will update the Lambda function to call **Amazon SNS**

- Open the file **wild-rydes-async-messaging/lab-1/unicorn-management-service/app.py**

```
sns = boto3.client('sns', config=config)
```

![Working with SNS](/images/2/2.6/0003.png?featherlight=false&width=90pc)

4. Next, we will put the item to DynamoDB

```
    response = sns.publish(
        TopicArn=TOPIC_ARN,
        Message=json.dumps(request),
        MessageAttributes = {
            'fare': {
                'DataType': 'Number',
                'StringValue': str(request['fare'])
            },
            'distance': {
                'DataType': 'Number',
                'StringValue': str(request['distance'])
            }
        }
    )
```

![Working with SNS](/images/2/2.6/0004.png?featherlight=false&width=90pc)

5. Update the template with the following command:

```
cd ~/environment/wild-rydes-async-messaging/lab-1
Sam build
```

![Working with SNS](/images/2/2.6/0005.png?featherlight=false&width=90pc)

6. After updating, we deploy with the following command:

```
sam deploy
```

![Working with SNS](/images/2/2.6/0006.png?featherlight=false&width=90pc)