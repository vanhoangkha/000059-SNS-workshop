---
title : "Working with SNS"
date : "`r Sys.Date()`"
weight : 1
chapter : false
---

# Working with SNS

#### Overview

As a registered customer, when you need a ride, you can use the Wild Rydes customer app to request a unicorn and manage everything around it. As a registered unicorn, you can use the Wild Rydes unicorn app to manage everything around your business.

In particular, unicorns are interested to use the app to submit a ride completion after they have successfully delivered a customer to their destination. This is the use case we will now have a closer look at.

At Wild Rydes, end-user clients typically communicate via REST APIs with the backend services. For our use case, the Wild Rydes unicorn app interacts with the API exposed by the unicorn management service. It uses the submit-ride-completion resource to send the relevant details of the ride to the backend. In response to that, the backend creates a new completed-ride resource and returns the respective status code, the location, and a representation of the new resource to the client.

It’s probably not a surprise that there are other services in the Wild Rydes microservices landscape, that are also interested in a new completed ride:

Customer notification service: Customers should get a notification into their app about their latest completed ride.
Customer accounting service: After all, Wild Rydes is a business, so this service would be responsible to collect the fare from the customer.
Extraordinary rides service: This is special service that is interested in rides with fares or distances above certain thresholds - preparing the respective data for marketeers and success managers.
This use case obviously cries for making use of publish/subscribe messaging, which can comfortably done using Amazon SNS in a serverless and scalable manner. It decouples both sides as much as possible. Services on the right hand side can autonomously subscribe to the topic, transparent to the left hand side.

![Working with SNS](/images/1/0000.png?featherlight=false&width=90pc)

{{% notice tip %}}
This hands-on lab will continue the story of the previous lab [Building a serverless web app Wild Rydes](https://000036.awsstudygroup.com/en)
{{% /notice %}}

#### Content

1. [Introduction](1-introduce/)
2. [Preparation steps](2-prerequiste/)
3. [Using SAM to deploy infrastructure](3-initstate/)
4. [Create Amazon SNS Topic](4-createsnstopic/)
5. [Create Customer notification service](5-createcnss/)
6. [Create Customer accounting service](6-create/)
7. [Create Extraordinary rides service](7-create/)
8. [Update Unicorn Management Service](8-update/)
9. [Fan-out test and message filtering](9-test/)
10. [Resource Cleanup](10-cleanup/)