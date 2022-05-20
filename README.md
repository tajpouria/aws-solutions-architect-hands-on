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

- [] Create and attach an EBS volume to an EC2 instance, [then format and mount it](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-using-volumes.html).
- [] Create different volume types.
- [] Create a Snapshot and Snapshot LifeCycle Policy.
- [] Migrate a volume to a different AZ. Make a Snapshot, and create a volume from it, to the target AZ.
- [] Encrypt an UnEncrypted EBS volume. Make a encrypted snapshot, create a encrypted volume from it, and reattach the encrypted volume.
- [] Create an EFS and mount it on two EC2 instances using [amazon-efs-utils](https://docs.aws.amazon.com/efs/latest/ug/installing-amazon-efs-utils.html).

## Resources

[awsboy.com](https://www.awsboy.com/)

## References

[ip-ranges.amazonaws.com](https://ip-ranges.amazonaws.com/ip-ranges.json)
