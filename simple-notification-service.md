# Simple Notification Services (SNS)
- Web service that makes it easy to set up, operate, and send notifications
- Highly scalable, flexible, cost-effective
- Publish messages from application for immediate delivery to subscribers or other applications
- Pushed-based message
- Push notifications available on:
  - Apple,
  - Google
  - Fire OS
  - Windows
  - Android in China, Baidu Cloud Push
- Delivery (subscribers)
  - HTTP
  - HTTPS
  - SMS
  - Email
  - Email-JSON
  - SQS queues
  - Application
  - Lambda
- Can trigger lambda functions
  - Lambda is triggered using message payload
    - Received as an input parameter
    - Can manipulate message, publish to other SNS topics or AWS services
- Mostly used in combination with CloudWatch and Autoscaling
  
## Topic
- Allows for grouping of multiple recipients
- Access point for allowing recipients to dynamically subscribe for identical copies fo the same notification
- One topic can support deliveries to multiple endpoint types
  - i.e. iOS, Android, and SMS together

|SNS|SQS|
|:---|:---|
|Messaging Service|Messaging Service|
|Push|Pull|

### Pricing
- $0.50 per 1 million requests
- $0.06 per 100,000 notification deliveries over HTTP
- $0.75 per 100 notifications over SMS
- $2.00 per 100,000 notifications over email