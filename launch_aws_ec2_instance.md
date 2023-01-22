# Launch AWS EC2 Instance

This document describes how to launch (create a new) AWS EC2 instance.

Primary source: [Tutorial: Get started with Amazon EC2 Linux instances]([Tutorial: Get started with Amazon EC2 Linux instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EC2_GetStarted.html#ec2-launch-instance_linux)

Go to: [AWS EC2 console](https://console.aws.amazon.com/ec2/)

*Important:* First, make sure the **Region** in the top navigation bar is set to the region you want to use and is used to create the key pair,
the security group, and the EC2 instance.

In the top center area of the page is Resources. Click on *Instances* under Resources.

Click on the *Launch instances* button in the top right of the page.

Enter/select the following:

* Name: AWS Node Server 1
* Application and OS Images (Amazon Machine Image): 
  * Quick start: Amazon Linux aws
  * Amazon Linux 2 AMI (HVM) - Kernel 5.10, SSD Volume Type - Free tier eligible
  * Architecture: 64-bit (x86)
* Instance type: t2.micro - Free tier eligible
* Key pair: select the [key pair previously created](aws_key_pair.md) from the selector.
* Network settings: 
  * VPC: use the one presented. It should be labeled *(default)*.
  * Subnet: No preference
  * Auto-assign public IP: Enable
  * Firewall (security groups): click *Select existing security group* and select the [security group previously created](aws_security_group.md) from the selector.
* Configure storage: 1 x 8 GiB gp2 (Note: says the 8 can be set up to 30 for free tier. This is the server's hard drive.)
* Advanced details: don't change anything.
* Summary: set *Number of instances* to 1.

Click the *Launch instance* button on the lower right of the page to create the new EC2 instance.
