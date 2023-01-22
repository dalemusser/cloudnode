# AWS Security Group

This document describes creating an AWS security group that establishes the firewall rules for the traffic allowed in and out of the server (what ports
are open or closed.)

Primary source: [Create a security group](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/get-set-up-for-amazon-ec2.html#create-a-base-security-group)

## Creating

Go to: [AWS EC2 console](https://console.aws.amazon.com/ec2/)

*Important:* First, make sure the **Region** in the top navigation bar is set to the region you want to use and is used to create the key pair,
the security group, and the EC2 instance. I recommend using "N. Virginia" which is "US East (N. Virginia) us-east-1".

In the menu on the left side of the page, choose *Security Groups* under *Network &amp; Security*.

Click the *Create security group* button at the top left of the page.

Under *Basic details* enter the following:

* Security group name: nodeserver1_SG_useast1
* Description: Allow web app and ssh access
* VPC: *use the info that is already there*

Note: it is recommended to put the region used in the security group name. "useast1" is based on the region being "US East (N. Virginia) us-east-1".

Under *Inbound rules* add the following rules:

* Click *Add rule* button to create rule to allow port 80 (http) from anywhere using IPv4
  * Type: Custom TCP, Protocol: TCP, Port range: 80, Source: Anywhere-IPv4
  * The above is saying open port 80 for http traffic via IPv4 from anywhere.


