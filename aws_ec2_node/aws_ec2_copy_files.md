# Copy Files from Workstation to EC2 Instance

This document describes how to copy files from a development workstation (the local computer) to an EC2 instance (the server).

## Using Secury Copy (scp)

To copy files to the server you can use ```scp``` at the command line. ```scp``` = secure copy. It uses ssl to securely copy files from one 
computer to another on the network.

When using *scp*, like when using *ssh*, a ```.pem``` file (private key) is needed to authenticate with the server. Make sure the rights on 
the ```.pem``` file  are set to 400 and it is put in a location where it can be easily accessed, but is also safe. In Terminal, use
```chmod 400 "AWS Node Server 1.pem"``` to set the rights. You must either be in the same directory as the ```.pem``` file or specify the path
to the ```.pem``` file in the command. 

Since your home directory is at ```~```, creating a ```keys``` directory in your home directory and putting the ```.pem``` file there, allows you
to use the following path to access it: ```"~/keys/AWS Node Server 1.pem"```

If I want to copy the files and directories from my current working directory (say, the project's directory) to the home folder on the server, use:

```
scp -r -i "~/keys/Dale Musser AWS1.pem" * ec2-user@techinnovator.online:
```

* ```-r``` means recursively go through and copy the directories
* ```*``` means copy all from the source directory
* ```:``` after IP address with nothing following means the home directory on the server

Copying all the files individually takes more time than zipping up the files, copying the zip file, and unzipping it on the server. The following
copies a zip file named staticapp.zip to the home directory on the server.

```
scp -i "~/keys/AWS Node Server 1.pem" staticapp.zip ec2-user@techinnovator.online:
```

See the [AWS Key Pair](aws_key_pair.md) page for more information on using ```scp```.

