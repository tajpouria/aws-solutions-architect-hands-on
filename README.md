# AWS Solutions Architect Associate Examples

A hands-on to-do list to practice the "[AWS Certified Solutions Architect – Associate](https://aws.amazon.com/certification/certified-solutions-architect-associate/)" exam objectives.

Introduction

- [✓] Setup a cost budget that sends an email alert as soon as 1 cent has been spent.

IAM and EC2

- [✓] Create an User and Admin group. Add the user to the Admin group.
- [✓] Create an EC2 instance.
- [✓] Create a simple private network using Security Groups.
- [✓] Allocate an Elastic IP and associate it with an instance.
- [✓] Install Apache2 on an EC2 instance using user data.
- [✓] Create an web server AMI and use it to launch an instance.
- [✓] Create all sorts of Place Groups and experiment with placing EC2 instances in them in the launch menu.
- [✓] Create an ENI and attach it to an instance.
- [✓] Create an instance with Hibernate stop, and Hibernate it.

ELB and ASG

- [✓] Create 3 EC2 instances and load balance HTTP traffic between them using CLB. Use the following script as user data:

```sh
#!/bin/bash
yum update -y
yum install -y httpd.x86_64
systemctl start httpd.service
systemctl enable httpd.service
echo "Hello World from $(hostname -f)" > /var/www/html/index.html
```

- [✓] Use ALB to load balance traffic between two target groups based on paths.
- [✓] Use NLB to load balance traffic between two target groups.
- [✓] Use ALB to load balance traffic between EC2 instances with stickiness enabled.
- [✓] Enable Cross Zone Load balancing in CLB configuration to load balance the traffic between multiple zone.
- [✓] Ringster a HTTPS listener ACM on a CLB, ALB and NLB.
- [✓] Enable Connection Draining (DeReregistration delay) in one of the ELBs.
- [✓] Configure a ASG with ALB, and adjust the desired capacity.
- [✓] Create different types of Scaling Policies, and Scheduled Actions to scale out/in instances.

EBS and EFS

- [✓] Create and attach an EBS volume to an EC2 instance, [then format and mount it](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-using-volumes.html).
- [✓] Create different volume types.
- [✓] Create a Snapshot and Snapshot LifeCycle Policy.
- [✓] Migrate a volume to a different AZ. Make a Snapshot, and create a volume from it, to the target AZ.
- [✓] Encrypt an UnEncrypted EBS volume. Make a encrypted snapshot, create a encrypted volume from it, and reattach the encrypted volume.
- [✓] Create an EFS and mount it on two EC2 instances using [amazon-efs-utils](https://docs.aws.amazon.com/efs/latest/ug/installing-amazon-efs-utils.html).

RDS, Aurora and, ElastiCache

- [✓] Create a DB subnet group then create a MySQL RDS instance inside it. Create read replica in the same AZ.
- [✓] Create an Aurora RDS instance, and configure replica auto scaling.
- [✓] Create a Redis Cluster and a Memcached ElastiCache instances.

Route 53

- [✓] Register a domain, Create an A record, and set a 2 minutes TTL for it.
- [✓] Create an Alias record that map the root domain (apex) to a subdomain.
- [✓] Create a A record with the Simple routing policy, and set the value to multiple IP addresses.
- [✓] Create 3 A records with different weights using Weighted routing policy, and set each record to point a different IP address.
- [✓] Create 3 A records, each one for a distinct region using Latency routing policy. Set each record to point to a IP address in the respective region.
- [✓] Create 2 Health Check for 2 distinct instances. Create 3 A records using Fail Over routing policy, associate 2 of them to primary instances with previously configured Health Check, and 1 to a secondary instance.
- [✓] Create 2 A records using GeoLocation routing policy, One to map the requests originated from north America continent, to an instance within us-north1, and the other one as the default response.
- [✓] Create 3 Health Check for 3 distinct instances. Create 3 A records using Multi Value routing policy, and them with previously configured Health Checks.

Elastic Beanstalk

- [✓] Deploy a sample application on a single instance using Beanstalk.

S3

- [✓] Create a S3 bucket, create a folder in it, and upload a file into that folder.
- [✓] Enable Versioning on a bucket, version an object, and mark an object as deleted.
- [✓] Upload two objects with SSE enabled, and use both KMS and S3 keys. Enable default SSE and upload another object.
- [✓] Create a bucket policy that prevents uploading unEncrypted objects using Policy Generator. Block public access to all S3 buckets on account level.
- [✓] Experiment with bucket and object ACLs.
- [✓] Host a static website, with two pages and one image on a bucket, and allow public access.
- [✓] Host two static websites, each one with one pages on two different buckets. Provide CORS access to the other website, in one of the websites permission settings. Fetch the allowed website and render its content in the other website.

CLI, SDK, IAM Roles and, Policies

- [✓] Install the AWS CLI.
- [✓] Configure the AWS CLI.
- [✓] Attach an IAM Role with AmazonS3FullAccess policy, to an EC2 instance. Use the CLI installed on instance to create, and remove a random S3 Bucket.
- [✓] `mb` a Bucket, `ls` the Buckets, `cp` a file from local to a Bucket, `ls` the content of a Bucket, `cp` a file a Bucket to local, `rb` a Bucket.
- [✓] Create a custom Policy for an attached to Role, that allows reading and writing to a specific folder on a S3 bucket. Test the Policy using Policy Simulator.
- [✓] Fetch an EC2 instance meta-data from `http://169.254.169.254/latest/meta-data`.

Advanced S3 and Athena

- [✓] Create a S3 Bucket with Versioning enabled. Configure a root profile on CLI. Enable MFA Delete for the Bucket. Upload a object and verify the MFA delete.

```sh
aws configure --profile <profile name>

# Enable S3 MFA delete
aws s3api put-bucket-versioning --bucket <bucket name>\
  --versioning-configuration Status=Enabled,MFADelete=Enabled\
  --mfa '<ARN of MFA device> <MFA code>'\
  --profile <profile name>


# List object versions
aws s3api list-object-versions \
  --profile <profile name> \
  -–bucket <bucket name> \
  -–key <object-key>

# Delete an object with MFA enabled
aws s3api delete-object \
  --profile root \
  --bucket advance-aws-and-athena \
  --version-id <version ID> \
  --key <object key> \
  --mfa '<ARN of MFA device> <MFA code>'

# Disable S3 MFA delete
aws s3api put-bucket-versioning --bucket <bucket name>\
  --versioning-configuration Status=Enabled,MFADelete=Disabled\
  --mfa '<ARN of MFA device> <MFA code>'\
  --profile <profile name>
```

- [✓] Enable server access logs for a Bucket and store the logs in S3.
- [✓] Create cross region replication (CRR) and same region replication (SRR) rules for a Bucket with delete marker replication enabled, and verify the upload and delete replications.
- [✓] Generate a pre-sign, ephemeral URL to access an object on S3.

```sh
aws s3 presign s3://<bucket name>/<object name> --expires-in 300 --region us-west-1

# Set the signature version in case of error.
aws configure set default.s3.signature_version s3v4
```

- [✓] Create objects in all different Storage classes and access those objects.
- [✓] Create a S3 lifecycle rule to satisfy the following transition: Create an object on Standard class, move it Standard Infrequent access (IA) after 30 days, move it to intelligent tiering after 70 days, move it to Glacier after 180 days and, finally move to Glacier deep archive after 365 days.
- [✓] Create a event notification for a S3 Bucket that writes events to SQS.
- [✓] [Analyze a S3 access logs bucket using Athena](https://aws.amazon.com/premiumsupport/knowledge-center/analyze-logs-athena/).

CloudFront and AWS Global Acceleration

- [✓] Configure CloudFront with a S3 bucket as the origin. Make sure the objects are only available from CDN using origin access identity (OAI).
- [✓] Configure Global Accelerator with two Endpoint groups, one in US and the other one in EU region, each one containing one EC2 instance.

AWS Storage Extras

- [✓] Order a Snowball to import date from on-premise data center to AWS.
- [✓] Create all types of Storage Gateways.
- [✓] Create AWS FSx for window and Lustre.

SQS, SNS, Kinesis and Amazon MQ

- [✓] Create a SQS queue with encryption enabled. Send messages to it and receive messages from it.
- [✓] Create a SQS queue with Visibility timeout of 40 seconds. Send messages to it and receive messages from it.
- [✓] Create a SQS queue and a Dead-letter queue (DLQ). Configure the Dead-letter queue for maximum of 3 receives with 5 seconds for Visibility timeout.
- [✓] Configure Delivery delay for a SQS queue. Send message with Delivery delay to it.
- [✓] Create a SQS FIFO queue. Send messages with order to it and receive messages from it.
- [✓] Create a SNS topic. Subscribe to it via Email. Send messages to topic and receive them via email.
- [✓] Fan-out a SNS input topic to two SQS queue.
- [✓] Create a Kinesis Data Stream with one Shard and interact with using the following AWS CLI:

```sh
aws kinesis list-streams

aws kinesis describe-stream --stream-name <stream name>

aws kinesis put-record \
  --stream-name <stream name> \
  --data '<data>' \
  --partition-key <partition key>

aws kinesis get-shard-iterator \
  --stream-name <stream name> \
  --shard-id <shard ID (From describe-stream)> \
  --shard-iterator-type <TRIM_HORIZON|AT_SEQUENCE_NUMBER|AFTER_SEQUENCE_NUMBER|AT_TIMESTAMP|LATEST (aws kinesis get-shard-iterator help)> \

aws kinesis get-records --shard-iterator '<shard iterator (aws kinesis get-shard-iterator help)>'
```

- [✓] Create an Amazon MQ with Apache Active MQ as the engine. Tune the security group and access the Active MQ management console. Create a queue and send message to it.

AWS Serverless

- [] Create a Lambda function from existing blueprint. Access and log the event properties on Lambda function. Make the Lambda function to raise an Error. Monitor the success and failed logs on Cloud watch.
- [] Create a DynamoDB table. Insert an item into it.
- [] AWS API gateway re watch ??

Networking - VPC

- [✓] Create a VPC with 2 CIDR blocks.
- [✓] Create 4 subnets in 2 different AZ with auto-assign IPv4 setting enabled. 2 public with smaller number of IPv4, and 2 private with more available IPv4.
- [✓] Create an internet gateway for VPC. Create 2 routing table and associate each one of them with public and private subnets.
- [✓] Create an EC2 instance in one of the public subnets. Tune the routing table and security groups to allow SSH into instance from outside and provide public internet access for the instance.
- [✓] Create an EC2 instance in on of the private subnets. Provision an [NAT instance](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_NAT_Instance.html) in one of the public subnets (Make sure [disable source/destination check](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_NAT_Instance.html#EIP_Disable_SrcDestCheck)). Tune the security group and routing table to allow: 1. SSH into instance from **private subnet**. 2. Allow HTTP, HTTPS, and ping from private instance to public internet.
- [✓] Replace the instance NAT gateway with an AWS NAT gateway.
- [] Enable DNS resolution settings (enableDnsSupport) and DNS hostname setting (enableDnsHostname) for the VPC. Create a private hosted zone (Route53). Create a CNAME record that resolves to [tajpouria.com](https://tajpouria.com).
- [] Install Apache web server on public instance. Create a NACL (Network Access Control List) rule that deny HTTP inbound traffic, then remove it. Create a NACL rule that deny all the outbound traffic, then remove it.
- [] Create another VPC with private subnet and a EC2 instance in it (Make sure the IP ranges is not overlapping with the exiting VPC). Peer two VPCs using VPC peering. Tune the routing tables rules on both VPCs that allows ping instances using their private IP addresses.
- [] Remove the routing rule that allow public internet access to a private instance. Create an IAM role that allows S3 full access and attach it to the private instance. Create an gateway endpoint that let the instance to access the S3 service. (Make sure include the gateway endpoint region to route the request correctly `aws s3 ls --regions eu-west-1`)
- [] Create a log group in Cloud Watch. Enable public VPC flow logs and store the logs in created log group. Capture the flow logs for a public instance. (Reset the internet access routing table rule that you removed in the previous step.)
- [] Enable public VPC flow logs and store the logs in a S3 bucket. Capture the flow logs for a public instance. [Query Amazon VPC flow logs](https://docs.aws.amazon.com/athena/latest/ug/vpc-flow-logs.html) using Athena.
- [] Create an egress-only internet gateway. Add a routing rule to route all the outgoing IPv6 requests (`::/0`) to egress-only gateway.

## Resources

- [Stephane Maarek](https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c02/)
- [Jon Bonso](https://www.udemy.com/course/aws-certified-solutions-architect-associate-amazon-practice-exams-saa-c03/)
- [awsboy.com](https://www.awsboy.com/aws-practice-exams/solutions-architect-associate/)

## References

- [ip-ranges.amazonaws.com](https://ip-ranges.amazonaws.com/ip-ranges.json)
- [evkalinin/awsping](https://hub.docker.com/r/evkalinin/awsping)
