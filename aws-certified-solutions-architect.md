### Definitions

**_Region_** A geographic area or physical location, e.g. Northern Virginia, Tokyo. Each _region_ consists of 2 or more availability zones.

**_Availability Zone_** Simply a data center. One or more discrete data centers, each with redundant power, networking and connectivity, housed in seperate facilities. Seperated far enough apart to be able to survive natural disasters, etc.

**_Edge Region_** Endpoints for AWS, used for caching content. Typically consists of Cloudfront (CDN). There are manay more _Edge Locations_ than _regions_.

### Services

#### Compute

**_EC2_** Elastic Compute Cloud, virtual or physical servers

**_EC2 Container Service_** Use for managing containers (Docker) in the Cloud

**_Elastic Beanstalk_** Used by developers to provision all pieces of infrastructure automatically

**_Lambda_** Serverless functions that execute code as needed without servers.

**_Lightsail_** Virtual private server service, base server provisioned with basic `ssh` access

**_Batch_** Batch computing in the cloud

#### Storage

**_S3 - Simple Storage Service_** Object based storage. Consists of 'buckets'

**_EFS - Elastic File System_** Network Attached Storage, allows files to be uploaded to and _EFS_ volume and mounted to multiple virtual machines

**_Glacier_** Data Archival, accessed very infrequently

**_Snowball_** Allows for bringing in large amounts of data by copying to a physical drive and sending to Amazon for copying to the cloud

**_Storage Gateway_** Virtual applicances setup in your data center or head office for copying data to _S3_

#### Databases

**_RDS - Relational Database Services_** Relational databases as a service, MySQL, Postgres, Aurora (Amazons MySQL)

**_DynamoDB_** Non-relational database

**_Elasticache_** Allows for caching commonly requested information from your DB servers

**_Redshift_** Data warehousing or Business Intelligence

#### Migration

**_AWS Migration Hub_** Tracking service that allows for tracking applications during the migration process

**_Application Discovery Service_** Automated set of tools for detecting applications and their dependencies

**_Database Migration Service_** Easy way to migrate DBs from on-prem to AWS

**_Server Migration Service_** Tool for migrating virtual and physical servers into the AWS cloud

**_Snowball_** Used for migrating large amounts of data through physical media, e.g. Terabytes +

#### Networking & Content Delivery

**_VPC - Virtual Private Cloud_** A virtual data center within AWS to wall off your infrastructure from the outside, includes firewalls, EXTREMLY IMPORTANT!!

**_CoudFront_** Content delivery network (CDN)

**_Route53_** Domain Name Service (DNS)

**_API Gateway_** Allows for creation of an API that other APIs/Services can communicate

**_Direct Connect_**  
Allows for a direct connection from a corporate office or data center into AWS, your VPC

#### Developer Tools

**_CodeStar_**  
A way of project managing your code, CD toolchain

**_CodeCommit_**  
A source control service for source repositories

**_CodeBuild_**  
Once code is commited, will compile, test, and generate deployable packages

**_CodeDeploy_**  
Automates code deployments to _EC2_, on-prem, or _Lambda_ instances

**_CodePipeline_**  
A continuous delivery (CD) service

**_X-Ray_**  
Used to analyze and debug serverless applications, includes request tracing to allow for identifying root causes of issues

**_Cloud9_**  
A cloud based IDE

#### Management Tools

**_CloudWatch_**  
Monitoring service

**_CloudFormation_**  
Scripting infrastructure

**_CloudTrail_**  
Logs any interaction in the AWS environment, turned on by default and stores records for one week

**_Config_**  
Point in time configurations of your AWS environment, allows for moving back to a configuration

**_OpsWorks_**  
Similar to _Elastic Beanstalk_ with more robust features using Chef and Puppet for automating environments

**_Service Catalog_**  
A catalog for services approved for use, typically seen in larger organizations. E.g. virtual machine images, OS, DBs, software, architecture

**_Systems Manager_**  
Interface for managing AWS resources. E.g. EC2, patch maintenance, grouping of resources

**_Trusted Advisor_**  
Gives advice across many different disciplines. Alerts to things like open ports, unused services

**_Managed Services_**  
AWS helps to manage various services, ex: EC2, with less interaction from client

#### Media Services

**_Elastic Transcoder_**  
Transcodes video content to work on various devices

**_Media Convert_**  
File based video transcoding service for broadcast, allows for video on demand

**_MediaLive_**  
Broadcast quality video processing service providing streams

**_MediaPackage_**  
Prepares and packages videos for delivery over internet

**_MediaStore_**  
Storage service optimized for media, can be used to deliver live and on-demand content

**_MediaTailor_**  
Allows for targeted advertising through video streams without sacrificing quality

#### Machine Learning

**_SageMaker_**  
Allows for developers to use deep learning

**_Comprehend_**  
Allows for knowing if users are saying good or bad things about your products

**_DeepLends_**  
Artificially aware camera without connecting to a backend

**_Lex_**  
Powers Amazon Alexa service, artifically aware way of communicating with customers

**_Machine Learning_**  
Less intelligent than deep learning. Uses a dataset provided to analyse results and provides a predicted outcome for new data provided.

**_Polly_**  
Converts text to speech

**_Rekognition_**  
Analyses photo and video, returns what is in the file, ex: dog, beach, ball, with percentages of accuracy

**_Amazon Translate_**  
Conversion of languages, similar to Google Translate

**_Amazon Transcribe_**  
Automated speech recognition for transcription

#### Analytics

**_Athena_**  
Allows for execution of SQL queries in S3 buckets

**_EMR - Elastic Map Reduce_**  
Used to process large amounts of data

**_CloudSearch_**  
**_ElasticSearch Service_**  
Search services

**_Kinesis_**  
Allows for ingesting large amounts of data into AWS, ex: find all examples of a hash tag being used

**_Kinesis Video Streams_**  


**_QuickSight_**  
Business Intelligence tool

**_Data Pipeline_**  
Allows for moving data between AWS services

**_Glue_**  
Used for ETL (Extract, Transform, and Load), used when moving data that may not be in the required shape before moving

#### Security & Identity & Compliance

**_IAM (Identity Access Management)_**  

**_Cognito_**  
Third-party mobile device authentication, ex: Facebook, Google. Once authenticated can request temporary access to AWS resources

**_GuardDuty_**  
Monitors for malicious activities on your AWS account

**_Inspector_**  
Agent install on VMs or EC2 for executing tests, ex: security vulnerabilities. Can be scheduled, returns a report with severity

**_Macie_**
Scans S3 buckets for PII (Personally Identifiable Information), provides an alert

**_Certificate Manager_**  
SSL certificate for free if registered through Route53

**_CloudHSM (Hardware Security Module)_**  
Hardware used to store keys, ex: public/private keys, encryption keys

**_Directory Service_**  
Integrating Microsoft AD services with AWS services

**_WAF (Web Appplication Firewall)_**  
Layer 7 firewall to prevent things like cross-site scripting, SQL injections

**_Shield_**  
DDOS mitigation, included with some AWS services (CloudFront)

**_Artifact_**  
Used for audit and compliance, on-demand reports, ex: SOC (Service Organization Control), PCI (Payment Card Industry) reports

#### Mobile Services

**_Mobile Hub_**  
Management console for mobile app(s) to ease in setup of mobile services within AWS

**_Pinpoint_**  
Targeted push notifications to drive engagement, ex: based on user location

**_AWS AppSync_**  
Auto updates web, mobile app data in real-time, offline data support

**_Device Farm_**  
Allows for testing apps on live devices

**_Mobile Analytics_**  
Analytics for mobile

#### AR (Augmented Reality) / VR (Virtual Reality)

**_Simarian_**  
(Beta) Set of tools for developing in AR/VR

#### Application Integration

**_Step Functions_**  
Helps to manage various Lambda functions and how to execute them

**_Amazon MQ_**  
Helps with message queues, similar to Rabbit MQ

**_SNS (Simple Notification Service)_**  
Notification service

**_SQS (Simple Queue Service)_**  
Queueing service for decoupleing infrastructure. Oldest AWS service.

**_SWF (Simple Workflow)_**  
A workflow service. Used in Amazon warehouses.

#### Customer Engagement  

**_Connect_**  
Contact center as a service, call center like functionality

**_Simple Email Service_**  
Email service

#### Business Productivity

**_Alexa for Business_**  
Ex: dial into meeting room, inform IT that a printer is broken

**_Chime_**  
Video conferencing with recording capabilities. Similar to Google Hangouts or Zoom meeting

**_Work Docs_**  
Similar to Dropbox.

**_WorkMail_**  
Similar to Office365 or Gmail

#### Desktop & App Streaming

**_Workspaces_**  
VDI (Virtual Desktop Interface) running in AWS then streamed to device

**_AppStream 2.0_**  
Streaming applications running in cloud

#### Internet of Things (IOT)  

**_iOT_**  
**_iOT Device Management_**  
Assists with managing many devices

**_Amazon FreeRTOS_**  
OS for microcontrollers

**_Greengrass_**  
Software for securing operation of iOT devices 

#### Game Development

**_GameLift_**  
Service for game development






























