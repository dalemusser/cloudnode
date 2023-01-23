# Logging Into AWS EC2 Instance (ssh)

This document describes how to use ```ssh``` to login to an AWS EC2 instance.

## Login to AWS EC2 Instance

To login to an EC2 instance from ```ssh``` is used.  ```ssh``` = secure shell. It uses ssl to allow secure communication between the workstation 
(local computer) and the EC2 instance (server).

When using *ssh*, like when using *scp*, a ```.pem``` file (private key) is needed to authenticate with the server. Make sure the rights on 
the ```.pem``` file  are set to 400 and it is put in a location where it can be easily accessed, but is also safe. In Terminal, use
```chmod 400 <path_to_pem_file>``` to set the rights.

Since your home directory is at ```~```, creating a ```keys``` directory in your home directory and putting the ```.pem``` file there, allows you
to use the following path to access it: ```"~/keys/<filename>.pem"```. Example: ```"~/keys/AWS Node Server 1.pem"```

Login to the server using Terminal and ```ssh```.

```ssh -i <pem-file-path> ec2-user@<ip-address>```

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

To delete the *known_hosts* file use:

```
rm ~/.ssh/known_hosts
```

To edit the *known_hosts* file use:

```
nano ~/.ssh/known_hosts
```

Note: crtrl-k cuts a line and ctrl-x exits and asks to save.

## Right After Login

When you login you may get a message like the following:

```
7 package(s) needed for security, out of 8 available
Run "sudo yum update" to apply all updates.
```

If you do, run the following command to update the system:

```
sudo yum update
```
