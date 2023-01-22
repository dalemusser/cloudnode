# AWS Key Pair

This document describes creating and using an AWS key pair.

Primary source: [Create a key pair](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/get-set-up-for-amazon-ec2.html#create-a-key-pair)

Assumptions: you already have an AWS account and are logged in.

## Creating

Go to: [AWS EC2 console](https://console.aws.amazon.com/ec2/)

*Important:* First, make sure the **Region** in the top navigation bar is set to the region you want to use and is used to create the key pair,
the security group, and the EC2 instance.

In the top center area of the page is Resources. Click on *Key pairs* under Resources.

On the Key pairs page click on the *Create key pair* button (top left).

Enter the following information in the *Create key pair* page:

* Name: AWS Node Server 1
* Key pair type: **RSA**
* Private key file format: **.pem**

Note: The Name can be anything descriptive that meets the naming rules on the page.

Click the *Create key pair* button.

A file, "AWS Node Server 1.pem", is downloaded. This is the private key that provides access to the server when using ssh to login or scp to copy files. 
This is the only time this file is provided/available. A copy of it must be securely kept.

The private key, .pem file, needs to have its rights set to "400" so that it is only readable by you and may not otherwise work for accessing the server.

In Terminal, use ```chmod 400 "AWS Node Server 1.pem"``` to set the rights.  You must either be in the same directory as the .pem file or specify the path to the .pem file in the command.

Store the .pem file in a safe place only you can access. The section on Using the key pair addresses where to put the .pem file to use it.

## Using

The private key (.pem file) that was created when the key pair was created is used to login to the server (ssh) or copy files to it (scp). 
The public key of the key pair is used when the server is created to establish the credentials for accessing the server.

To login to the server in a Terminal using ssh:

```ssh -i "AWS Node Server 1.pem" ec2-user@<ip-address>```

The above command assumes that the .pem file is in the same directory as the current working directory (where you are when you enter the ssh command).
It is useful to put the .pem file in a place where it is easy to access no matter what the current working directory is. Since your home directory is 
at ~, creating a *keys* directory in your home directory and putting the .pem file there, allows you to use the following command from anywhere to 
ssh into the server:

```ssh -i "~/keys/AWS Node Server 1.pem" ec2-user@<ip-address>```

Notice that the user is "ec2-user". This is the default user name used when an account is created for a new EC2 instance.

<ip-address> is where either the IPV4 numerical address or the domain name goes.

To copy files from your local computer to the server in a Terminal using scp:

```scp -i <path-to-pem-file> <path-to-files> <user-id>@<ip-address>:<destination-path-on-server>```

Example:

```scp -i "~/keys/AWS Node Server 1.pem" staticapp.zip ec2-user@techinnovator.online:``` copies staticapp.zip from the current local directory to the home directory on the server.

scp documentation:

* in the Terminal: man scp (on web at: [scp(1) - Linux man page](https://linux.die.net/man/1/scp)
* [scp Linux command](https://www.garron.me/en/articles/scp.html) (garron.me)
* [How to Use SCP Command to Securely Transfer Files](https://linuxize.com/post/how-to-use-scp-command-to-securely-transfer-files/) (linuxize.com)


