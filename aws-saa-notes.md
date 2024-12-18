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




