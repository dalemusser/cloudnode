# Node/Express App on AWS EC2

This document describes setting up an AWS EC2 instance and running a node/express application.

The following documents were the primary sources used to determine the process.

* [Tutorial: Setting Up Node.js on an Amazon EC2 Instance](https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/setting-up-node-on-ec2-instance.html) (AWS)
* [How to Deploy a Node.js Application On AWS EC2 Server](https://ourcodeworld.com/articles/read/977/how-to-deploy-a-node-js-application-on-aws-ec2-server) (ourcodeworld.com)

---

### Needed Before Launching (Creating) EC2 Instance

A key pair and a security group must be created before launching an EC2 instance. The key pair is used for authentication when logging in via a terminal. The security group establishes the firewall rules that determine what traffic is allowed in/out (what ports are open/closed).



