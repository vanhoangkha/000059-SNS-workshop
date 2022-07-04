---
title : "Cập nhật Unicorn Management Service"
date :  "`r Sys.Date()`" 
weight : 8
chapter : false
pre : " <b> 8. </b> "
---

#### Cập nhật Unicorn Management Service

Sau khi tạo SNS Topic và các subscription theo kiến trúc:


![Working with SNS](/images/1/0000.png?featherlight=false&width=90pc)

1. Trước hết chúng ta cấp IAM permission đến Lambda

- Cập nhật SAM template **wild-rydes-async-messaging/lab-1/template.yaml**

```
- SNSPublishMessagePolicy:
    TopicName: !GetAtt RideCompletionTopic.TopicName
```

![Working with SNS](/images/2/2.6/0001.png?featherlight=false&width=90pc)

2. Tiếp theo chúng ta phải cấp **Amazon SNS topic ARN** đến Lambda.

- Tiếp tục cập nhật SAM template **wild-rydes-async-messaging/lab-1/template.yaml**

```
TOPIC_ARN: !Ref RideCompletionTopic
```

![Working with SNS](/images/2/2.6/0002.png?featherlight=false&width=90pc)

3. Sau đó, chúng ta sẽ cập nhật Lambda function để gọi đến **Amazon SNS**

- Mở file **wild-rydes-async-messaging/lab-1/unicorn-management-service/app.py**

```
sns = boto3.client('sns', config=config)
```

![Working with SNS](/images/2/2.6/0003.png?featherlight=false&width=90pc)

4. Tiếp đến, chúng ta sẽ put item đến DynamoDB 

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

5. Cập nhật template bằng lệnh sau:

```
cd ~/environment/wild-rydes-async-messaging/lab-1
sam build
```

![Working with SNS](/images/2/2.6/0005.png?featherlight=false&width=90pc)

6. Sau khi cập nhật, chúng ta triển khai bằng lệnh sau:

```
sam deploy
```

![Working with SNS](/images/2/2.6/0006.png?featherlight=false&width=90pc)

