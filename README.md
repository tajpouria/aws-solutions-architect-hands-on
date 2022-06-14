# AWS Solutions Architect Associate Examples

A set of hands-on examples that covers the "[AWS Certified Solutions Architect – Associate](https://aws.amazon.com/certification/certified-solutions-architect-associate/)" exam objectives.

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

- [✓] Create 3 EC2 instances and load balance HTTP traffic between them using CLB.
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

- [] Deploy a sample application on a single instance using Beanstalk.

S3

- [] Create a S3 bucket, create a folder in it, and upload a file into that folder.
- [] Enable Versioning on a bucket, version an object, and mark an object as deleted.
- [] Upload two objects with SSE enabled, and use both KMS and S3 keys. Enable default SSE and upload another object.
- [] Create a bucket policy that prevents uploading unencrypted objects using Policy Generator. Block public access to all S3 buckets on account level.
- [] Experiment with bucket and object ACLs.
- [] Host a static website, with two pages and one image on a bucket, and allow public access.
- [] Host two static websites, each one with one pages on two different buckets. Provide CORS access to the other website, in one of the websites permission settings. Fetch the allowed website and render its content in the other website.

## Resources

- [Stephane Maarek](https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c02/)
- [Jon Bonso](https://www.udemy.com/course/aws-certified-solutions-architect-associate-amazon-practice-exams-saa-c03/)
- [awsboy.com](https://www.awsboy.com/aws-practice-exams/solutions-architect-associate/)

## References

- [ip-ranges.amazonaws.com](https://ip-ranges.amazonaws.com/ip-ranges.json)
