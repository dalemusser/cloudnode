# AWS Elastic IP Address

This document describes allocating and assigning an AWS Elastic IP address.

Go to: [AWS EC2 console](https://console.aws.amazon.com/ec2/)

*Important:* First, make sure the **Region** in the top navigation bar is set to the region you want to use and is used to create the key pair,
the security group, and the EC2 instance.

Go to *Elastic IPs* under *Network & Security* in the menu on the left side of the page.

Click on the *Allocate Elastic IP address* button in the upper right of the page.

Select the following on the *Allocate Elastic IP address* page.

 * Network Border Group: this should be set to the chosen region. Example: us-east-1 (It needs to be the same as the key pair, security group, and EC2 instance).
 * Public IPv4 address pool: Amazon's pool of IPv4 addresses
 * Global static IP addresses/Create accelerator: don't use
 * Tags: don't use

Click on the *Allocate* button on the lower right to allocate the IP address.
