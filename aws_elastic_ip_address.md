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

After the AWS Elastic IP address is created, go to the list of Elastic IPs by selecting *Elastic IPs* from the *Resources* area in the top center of the [AWS EC2 console](https://console.aws.amazon.com/ec2/).

Click on the *Allocated IPv4 address* in the list of *Elastic IP addresses*.

Click on the *Associate Elastic IP address* button on the top right of the page.

Select the following on the *Associate Elastic IP address* page:

* Resource type: Instance
* Instance: click in the selector and choose the EC2 instance previously launched.
* Private IP address: click in the *Choose a private IP address* selector and choose the IP address that appears.
* Reassociation: leave *Allow this Elastic IP address to be reassociated* unchecked.


