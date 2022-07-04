---
title : "Clean up resources"
date : "`r Sys.Date()`"
weight : 10
chapter : false
pre : " <b> 10. </b> "
---

#### Clean up resources

#### Delete AWS SAM template

1. Go to the AWS Cloud9 interface
2. Run the following command:

```
cd ~/environment/wild-rydes-async-messaging/lab-1
aws cloudformation delete-stack \
    --stack-name wild-rydes-async-msg-1
```