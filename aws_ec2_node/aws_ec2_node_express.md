# Node/Express App on AWS EC2

This document describes setting up an AWS EC2 instance and running a node/express application.

The following documents were the primary sources used to determine the process.

* [Tutorial: Setting Up Node.js on an Amazon EC2 Instance](https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/setting-up-node-on-ec2-instance.html) (AWS)
* [How to Deploy a Node.js Application On AWS EC2 Server](https://ourcodeworld.com/articles/read/977/how-to-deploy-a-node-js-application-on-aws-ec2-server) (ourcodeworld.com)

---

## Needed Before Launching (Creating) EC2 Instance

A key pair and a security group must be created before launching an EC2 instance. The key pair is used for authentication when logging in via a Terminal/ssh. The security group establishes the firewall rules that determine what traffic is allowed in/out (what ports are open/closed) on the server. The security group needs to allow traffic for http (port 80) and https (port 443) for the app to be reachable and ssh (port 22) so a connection can be make to the server using the Terminal/ssh to login.

Primary source: [Set up to use Amazon EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/get-set-up-for-amazon-ec2.html) (AWS)

* [AWS Key Pair](aws_key_pair.md)
* [AWS Security Group](aws_security_group.md)


## Launching (Creating New) EC2 Instance

Primary source: [Tutorial: Get started with Amazon EC2 Linux instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EC2_GetStarted.html#ec2-launch-instance_linux)

* [Launch AWS EC2 Instance](launch_aws_ec2_instance.md)

## Allocating and Assigning Elastic IP Address

* [Allocate and Assign Elastic IP Address](aws_elastic_ip_address.md)

## Setting DNS Record to Assign IP to Domain Name

* [Create DNS Record](create_dns_record.md)

---
## Needed Skills Before Proceeding

The following cover how to login to the EC2 instance (server) using ssh and how to copy files from the local workstation to the server.
The ability to do these two things is needed for the steps that follow.

* [Logging Into AWS EC2 Instance (ssh)](aws_ec2_ssh.md)
* [Copying Files from Workstation to EC2 Instance (scp)](aws_ec2_copy_files.md)

---

## Installing Node on Amazon Linux 2 on AWS EC2 Instance

* [Installing Node on Amazon Linux 2 on AWS EC2 Instance](aws_ec2_amazonlinux2_node.md)

## Installing Node/Express App on EC2 Instance

* [Install Node/Express App on EC2 Instance](aws_install_node_express_ec2.md)






