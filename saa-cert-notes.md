1. Data Centre > Availability Zone > Region

2. AWS ensures data is secure by redundancy. We store store content on data 
centres, AWS ensures redundancy by saving it to another DC through redundant 
high speed low latency links. This way if the 1st DC goes down the 2nd one
is up and running. This cluster of DCs are called Availability Zone.

Similarly cluster of AZs make a Region all the AZs in a Region are 
connected by `redundant` `high speed`, `low latency links`.

Which region to choose. There are 4 basic aspect you need to consider 
for this:
    a. Compliance
    b. Latency
    c. Pricing
    d. Service availability

3. Edge Location where data is cached so that you don't have to download 
any content every now and then. It will be stored near your location.



# Stephane Maarek from Udemy

## 3 - Getting Started with AWS

4. Global Services of AWS
    a. IAM
    b. Route53
    c. CloudFront (CDN)
    d. WAF (Web Application Firewall)

5. Most AWS services are Region-Specific:
    a. EC2 (IaaS)
    b. E Beanstalk (PaaS)
    c. Lambda (Func. as a Service)
    d. Rekognition (Softw. as a Service)

9 - Tour of AWS Console Services in AWS

6. You can go to global infrastructure regional product service link to find out which regions have which services.Remember that not all services are available in every region.

# 4 - IAM AWS CLI

## 11 - IAM Introduction Users Groups Policies

7. You should not use the root account and create a user from the root user instead. Preferable an `Admin` account from where you should use you AWS account
8. Users can be added into `Groups`. Groups Only contain user- remember that. A user can belong to multiple group.
9. Users or Groups can be assigned JSON documents called policies.
10. Policies define the permissions of the `Users`.
11. In AWS you apply the `least privilege principle`: don't give more permissions than a user needs.
12. IAM is a Global Service.
13. We can create an alias for our account ID and can use that link to sign in directly. This link will be a direct link. Like : https://zaman-aws-v2.signin.aws.amazon.com/console

## 12 - IAM Users Groups Hands On

13. We can create an alias for our account ID and can use that link to sign in directly. This link will be a direct link. Like : https://zaman-aws-v2.signin.aws.amazon.com/console

## 13 - IAM Policies

14. All the policies of a Group will be inherited by the Users in the group
15. You can also attach a User with an inline policy if it's not a part of 
a group.
16. Ref. the slides

Skipping to write other lecture because decided to use the slides

## 23 - AWS CloudShell

17. CloudShell can be used in place of AWS ClI on your machine

# 5 - EC2 Fundamentals

## 31 - EC2 Basics

18. EC2 is IaaS

19. OS we can we choose Linux Windows Mc OS
20. CPU RAM
21. Storage: 
    - Network Attached EBS & EFS
    - hardware EC2 Instance store
22. Network card: Speed of the card, Public IP address
23. Firewall rules: Sg
24. Bootstarp script (configure at first launch): EC2 User Data
25. The EC2 User Data Script runs with the root user (This script will be 
executed only once).
26. Types of instances

## 33 - EC2 Instance Types Basics
27. Instance comparison website:
     instances.vantage.sh

## 38 - How to SSH using Windows
28. To SSH from Windows <8 we can use Putty. In this case, we use .ppk 
format of the keys.

## 6 - EC2 Solutions Architect Associate Level
46. One account can have only 5 elastic IP addresses





















# SQS
Messaging: When we deploy multiple apps, they will need to communicate with each other.
There are two patteerns of the app communication:
    a. Synchronous Communication (app to app) \
    b. Asynchronous/ Event Based (app to queue to app)

    Understanding with a few lines:
    a. Synchronous between apps can be problematic if there are sudden spikes of traffic
    b what is you need to suddenly encode 1000 videos but usually it's 10?
    b. In that case, it's better to decouple your apps:
        i. using SQS: queue model
        ii. using SNS: pub/sub model
        iii. unsing Kinesis: real-time streaming model

Amazon SQS. What is a queue?

![alt text](sqs1-1.png)

Amazon SQS - Standard Queue
a. Fully managed service, used to decouple apps
b. Attributes:
    i. Unlimited throughput, unlimited no. of msgs in queue
    ii. Default retention of msgs: 4 days, maximum of 14 days
    iii. Low Latency (<10 ms on publish and receive)
    iv. Limitation of 256KB per msg sent
c. Can have duplicate msgs (at least once delivery, occasionally)
d. Can have out of order msgs

Ref. slide in this same directory. Time is short. Page number 382

# Section 19: Serverless Overviews from a Solution Architect Perspective

## 215. About the Serverless Section

Not so important
Main things:

1. In serverless, developers don't have to manage servers. We deploy `code`. We deploy 
`functions`.

## 216. Serverless Introduction

1. Serverless in AWS:
    - AWS Lambda
    - DynamoDB
    - AWS Cognito
    - AWS API Gateway
    - Amazon S3
    - AWS SNS & SQS
    - AWS Kinesis Dta Firehose
    - Aurora Serverless
    - Step Functions
    - Fargate

## 217. Lambda Overview

1. Why AWS Lambda

    In Amazon EC2:
    - Virtual Servers in the Cloud
    - Limited by the RAM and CPU
    - Continuously running
    - Scaling means intervention to add/remove servers

    In Amazon Lambda:
    - Virtual functions - no servers to manage
    - Limited by time - short executions
    - Run on-demand
    - Scaling is automated

2. Benefits:
    - Easy Pricing
        - Pay per request and compute time
        - Free tier of 1,000,000 AWS Lambda requests and 4000,000 GBs of compute time
    - Integrated with the whole AWS suite of services
    - Integrated with many programming languages
    - Easy monitoring through AWS CloudWatch
    - Easy to get more resources per functions (up to 10GB of RAM!)
    - Increasing RAM will also improve CPU and network.

    AWS Lambda language support
    - Node.js (JavaScript)
    - Python
    - Java
    - C# (.NET Core)/Powershell
    - Ruby
    - Custom Runtime API (Community supported, example Rust or Golang)
    - Lambda Container Image
        - The container image must implement the Lambda Runtime API
        - ECS/Fargate is preferred for running arbitrary Docker images

    AWS Lambda Integrations - Main Ones
    API Gateway - This is to create APIs and invoke Lambda functions
    Kinesis - Will be used in Lambda to do some data transformation on the fly.
    DynamoDB - will be used to create some triggers whenever somethings happens on our 
    database, a Lambda function will be triggered.
    S3 - A lambda function will be triggered whenever a file is created on our s3.
    Cloudfront - This will be attached to lambda 
    CloudWatch Events EventBridge - This is whenever things happen and our infrastructure on AWS
    and we want to be able to react to things. E.g., say, we have code pipeline state changes
    and we want to do some automation based on it, we can use a Lambda function.
    CloudWatch Logs - to stream the logs wherever you want
    SNS - to reach to notifications in your SNS topics
    SQS - to process msgs from your SQS queues.
    Cognito - handles user authentication and authorisation whenever user logs in to database

    Example: Serverless Thumbnail creation

    We can create a trigger for Lambda to create a thumbnail when an image is uploaded in S3
    so new thumbnail is created and with this trigger the lambda function 

    Example: Serverless CRON Job

    We can create a CloudWatch Event that will be triggered everyone hour

## 218. Lambda Hands-on

After 1 million you get cost

Explained how lambda works

## 219. Lambda Limits

AWS Lambda Limits to know - per region

Execution:
    - Memory allocation: 128 MB - 10GB (1 MB increments)
    - Maximum execution time: 900 seconds (15 minutes)
    - Environment variables (4 KB)
    - Disk capacity in the "function container" (in /tmp): 512 MB to 10GB 
    - Concurrency executions: 1000 (can be increased)
Deployment:
    - Lambda function deployment size (compressed .zip): 50 MB
    - Size of uncompressed deployment (code + dependencies): 250 MB
    - Can use the /tmp directory to load other files at startup
    - Size of environment variables: 4 KB

## 220. Lambda SnapStart

- Improves your Lambda functions performance up to 10x at no extra cost for Java 11 and above
- When enabled, function is invoked from a pre-initialized state (no function initialization from scratch)
- When you publish a new version:
    - Lambda initializes your function
    - Takes a snapshot of memory and disk state of the initialized function
    - Snapshot is cached for low-latency access

## 221. Customization at The Edge

- Many modern applications execute some form of the logic at the edge
- Edge Function:
    - A code that you write and attach to CloudFront distributions
    - Runs close to your users to minimize latency
- CloudFront provides two types: CloudFront Functions & Lambda@Edge
- You don't have to manage any servers, deployed globally
- Use case: Customize the CDN content
- Pay only for what you use
- Fully serverless

### CloudFront Functions & Lambda@Edge Use Cases




    

