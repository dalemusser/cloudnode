# Node/Express App on AWS EC2

This document describes setting up an AWS EC2 instance and running a node/express application.

The following documents were the primary sources used to determine the process.

* [Tutorial: Setting Up Node.js on an Amazon EC2 Instance](https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/setting-up-node-on-ec2-instance.html) (AWS)
* [How to Deploy a Node.js Application On AWS EC2 Server](https://ourcodeworld.com/articles/read/977/how-to-deploy-a-node-js-application-on-aws-ec2-server) (ourcodeworld.com)

---

### Needed Before Launching (Creating) EC2 Instance

A key pair and a security group must be created before launching an EC2 instance. The key pair is used for authentication when logging in via a Terminal/ssh. The security group establishes the firewall rules that determine what traffic is allowed in/out (what ports are open/closed) on the server. The security group needs to allow traffic for http (port 80) and https (port 443) for the app to be reachable and ssh (port 22) so a connection can be make to the server using the Terminal/ssh to login.

Primary source: [Set up to use Amazon EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/get-set-up-for-amazon-ec2.html) (AWS)

* [AWS Key Pair](aws_key_pair.md)



