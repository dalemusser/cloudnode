# AWS Security Group

This document describes creating an AWS security group that establishes the firewall rules for the traffic allowed in and out of the server (what ports
are open or closed.)

Primary source: [Create a security group](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/get-set-up-for-amazon-ec2.html#create-a-base-security-group)

## Creating

Assumptions: you already have an AWS account and are logged in.

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

* Click *Add rule* button to create rule to allow incoming traffic on port 80 (http) from anywhere using IPv4.
  * Type: HTTP, Protocol: TCP, Port range: 80, Source: Anywhere-IPv4
* Click *Add rule* button to create rule to allow incoming traffic on port 443 (https) from anywhere using IPv4.
  * Type: HTTPS, Protocol: TCP, Port range: 443, Source: Anywhere-IPv4
* Click *Add rule* button to create rule to allow incoming traffic on port 22 (ssh/scp) from anywhere using IPv4. (See note below!)
  * Type: SSH, Protocol: TCP, Port range: 22, Source: Anywhere-IPv4

Click the *Create security group* button at the bottom right to create the security group.

Note: setting the Source for SSH to Anywhere-IPv4 means the client computer can have any IPv4 address and access the server using ssh.
For better security the Source can be set to the specific public IPv4 address of the client computer (your development workstation).
This only works if your workstation has a public IP address or you know the public IP address of the LAN's gateway. Setting a specific IP address
makes it difficult to use a computer from different locations...like a laptop that is used in multiple locations and has different IP addresses in each.

You will select the security group you have created when you launch a new EC2 instance.
