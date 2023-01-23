# Install Node/Express App on EC2 Instance

This document describes installing a node/express app on an AWS EC2 instance.

## Login to AWS EC2 Instance

Login to the server using Terminal and ssh.

```ssh -i "~/keys/AWS Node Server 1.pem" ec2-user@<ip-address>```

Examples:

```ssh -i "~/keys/AWS Node Server 1.pem" ec2-user@techinnovator.online```<br/>
```ssh -i "~/keys/AWS Node Server 1.pem" ec2-user@3.222.14.12```

When you connect the first time it will ask if you want to continue connecting. You should answer: yes. This will add the host (server)
to the known hosts located in ```~/.ssh/known_hosts```. ```~``` is your home directory on your local workstastion.

```
ssh -i "~/keys/AWS Node Server 1.pem" ec2-user@techinnovator.online 

The authenticity of host 'techinnovator.online (3.222.14.12)' can't be established.
ED25519 key fingerprint is SHA256:8dkmBLBF3fm1gfJBzCiMaXw8SviSgBMo/TSu1/pmDqs.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'techinnovator.online' (ED25519) to the list of known hosts.
```

If you've connected before and the server is different than previously accessed (like if you kill your old instance and create a new one), 
you will get the following message.

```
ssh -i "~/keys/Dale Musser AWS1.pem" ec2-user@techinnovator.online 
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the ED25519 key sent by the remote host is
SHA256:8dkmBLBF3fm1gfJBzCiMaXw8SviSgBMo/TSu1/pmDqs.
Please contact your system administrator.
Add correct host key in /Users/musserda/.ssh/known_hosts to get rid of this message.
Offending ECDSA key in /Users/musserda/.ssh/known_hosts:5
Host key for techinnovator.online has changed and you have requested strict checking.
Host key verification failed.
```

To be able to log in after this happens you will need to delete the old record from ```~/.ssh/known_hosts```.  You can do that by either
editing the file using something like *nano* and find the line and delete it OR you can just delete the whole ```known_hosts``` file. If you 
delete the file it will just ask again if you want to connect like you did the first time for any server that was in the list.

## Copy Node/Express App to EC2 Instance

To copy the node/express app to the server you can use ```scp``` at the command line. scp = secure copy. It uses ssl to securely copy files from one 
computer to another on the network.

If I want to copy the files and directories from my current working directory (say, the project's directory) to the home folder on the server, use:

```
scp -r -i "~/keys/Dale Musser AWS1.pem" * ec2-user@techinnovator.online:
```

* -r = recursively go through and copy the directories
* \* copy all from the source directory
* : after IP address with nothing following means the home directory on the server

Copying all the files individually takes more time than zipping up the files, copying the zip file, and unzipping it on the server. The following
copies a zip file named staticapp.zip to the home directory on the server.

```
scp -i "~/keys/AWS Node Server 1.pem" staticapp.zip ec2-user@techinnovator.online:
```

See the [AWS Key Pair](aws_key_pair.md) page for more information on using ```scp```.

The goal is to get the files for the node/express app project on the server.  The files can be placed in the home directory or for supporting
experimenting with multiple app versions, you can put the files in a folder in the home directory.


NOTE: this is where I am currently in creating this document.

Remaining:

* Configuration to support access to port 80 and 443

* Installing node and express

* Installing and using pm2

* Connecting to the app

* Creating an app that support https



