# Logging Into AWS EC2 Instance

This document describes how to use to login to an AWS EC2 instance.

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

