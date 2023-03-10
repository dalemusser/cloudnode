# Installing Node on Amazon Linux 2 on AWS EC2 Instance

This document describes the installation of node and express on Amazon Linux on an AWS EC2 instance.

*Primary source:* [Tutorial: Setting Up Node.js on an Amazon EC2 Instance](https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/setting-up-node-on-ec2-instance.html)

---

*Assumptions:* you are logged into the instance using ssh in Terminal.

Before installing sofware, update the system if it is not up-to-date.  When you login, a message like the following may appear:

```
7 package(s) needed for security, out of 8 available
Run "sudo yum update" to apply all updates.
```

If it does, run:

```
"sudo yum update
```


*Important:* Amazon Linux 2 does not currently support the current LTS release (version 18.x) of Node.js. Use version 16.x instead.
From [NodeSource Node.js Binary Distributions](https://github.com/nodesource/distributions/blob/master/README.md#rpm):
![node on Amazon Linux](node_on_amazon_linux.png)

The following covers installation of Node.js 16.x.

Install the node version manager (nvm):

```curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash```

Activate nvm:

```. ~/.nvm/nvm.sh```

Use nvm to install Node.js 16.x:

```nvm install 16```

To run ```nvm``` and get its version number:

```nvm -v```

Test that node can evaluate a line of JavaScript:

```node -e "console.log('Running Node.js ' + process.version)"```

It should display:

```Running Node.js VERSION```



