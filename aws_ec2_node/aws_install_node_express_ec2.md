# Install Node/Express App on EC2 Instance

This document describes installing a node/express app on an AWS EC2 instance and configuring it to run.

## Copy Node/Express App to EC2 Instance

To copy the node/express app (project directory) to the server you can use ```scp``` at the command line. ```scp``` is used to securely copy files from your local workstation to the EC2 instance (server). See: [Copying Files from Workstation to EC2 Instance (scp)](aws_ec2_copy_files.md)

The following example assumes there is a project directory called *myapp* on the local workstation and it is to be placed in a directory called 
*myapp* on the server. It also assumes the ```pem``` file is at ```"~/keys/AWS Node Server 1.pem"``` and the domain name of the server is ```techinnovator.online```.

On the local workstation, from the directory holding *myapp*, zip *myapp* to create *myapp.zip*:

```zip -r myapp.zip myapp```

On the local workstation, from the directory holding *myapp.zip*, copy it to the server:

```scp -i "~/keys/AWS Node Server 1.pem" myapp.zip ec2-user@techinnovator.online:```

On the server, unzip *myapp.zip* in the home directory:

```unzip myapp.zip```

There should now be a *myapp* directory in the home directory containing the node/express app.









NOTE: this is where I am currently in creating this document.

Remaining:

* Configuration to support access to port 80 and 443

* Installing node and express

* Installing and using pm2

* Connecting to the app

* Creating an app that support https



