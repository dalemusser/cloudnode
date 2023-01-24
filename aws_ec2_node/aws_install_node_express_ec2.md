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

There should now be a *myapp* directory in the home directory containing the node/express app. In that directory is the 
```.js``` file for starting the node app. Typically it is something like ```index.js``` or ```app.js```.  For this documentation, 
```index.js``` is used.

You *could* now go into the *myapp* directory and run the node app by executing ```node index.js```. Before running the app,
there is an issue with it being able to bind to (use) port 80 and port 443. Port number below 1024 are
special in that normal users are not allowed to run servers on them. The app needs to be run as admin using ```sudo``` to
bind to ports 80 and/or 443. BUT!!!!!!, apps should not be run with ```sudo```; they should not be given admin rights. There are
real security problems with running an app as admin. The following is what is displayed when running a node app trying to 
bind to port 80.

```
[ec2-user@ip-172-31-88-127 staticapp]$ node index.js
node:events:491
      throw er; // Unhandled 'error' event
      ^

Error: listen EACCES: permission denied 0.0.0.0:80
    at Server.setupListenHandle [as _listen2] (node:net:1446:21)
    at listenInCluster (node:net:1511:12)
    at Server.listen (node:net:1599:7)
    at Function.listen (/home/ec2-user/staticapp/node_modules/express/lib/application.js:635:24)
    at Object.<anonymous> (/home/ec2-user/staticapp/index.js:11:5)
    at Module._compile (node:internal/modules/cjs/loader:1165:14)
    at Object.Module._extensions..js (node:internal/modules/cjs/loader:1219:10)
    at Module.load (node:internal/modules/cjs/loader:1043:32)
    at Function.Module._load (node:internal/modules/cjs/loader:878:12)
    at Function.executeUserEntryPoint [as runMain] (node:internal/modules/run_main:81:12)
Emitted 'error' event on Server instance at:
    at emitErrorNT (node:net:1490:8)
    at processTicksAndRejections (node:internal/process/task_queues:83:21) {
  code: 'EACCES',
  errno: -13,
  syscall: 'listen',
  address: '0.0.0.0',
  port: 80
}
```

The next steps makes it possible for the node app to bind to ports less than 1024. If your app isn't running on a port
less than 1024 (port 80 or 443 for example), then the ```setcap``` command that follows doesn't need to be run.

First, determine where node is installed. ```which node``` can be used to determine this.

```which node```

The following is an example of a path that may be returned. Copy the path **you receive** for your node installation.

```~/.nvm/versions/node/v16.19.0/bin/node```

Next, execute the following command to give the ```node``` app permission to use ports less than 1024 (port 80 in our case):

```sudo setcap cap_net_bind_service=+ep <path-to-node>```

Example using the demonstration path from ```which node```:

```sudo setcap cap_net_bind_service=+ep ~/.nvm/versions/node/v16.19.0/bin/node```

Note: If ```node``` is replaced or updated, the above command must be executed on the new copy of ```node``` to re-establish the permission to be allowed to access ports less than 1024.

Now, the node/express app can be run and tested using:

```node index.js```

If there are no issues, a message like the following is displayed.

```
[ec2-user@ip-172-31-88-127 staticapp]$ node index.js
Example app listening on port 80
```
...and the cursor is hanging out on the next line. If we close the Terminal or ctrl-c out of the app, the app will stop. 
So, this way of running the app only works for testing. In the next steps ```pm2``` (process manager 2) is used to run the app
so it will keep running when the Terminal is closed.

With the app running, put the URL for the app, ```http://<domain-name>```, in the browser and see if the app responds. For example,
with my app at *techinnovator.online* I go to ```http://techinnovator.online``` and get "Hello World!" in the browser. If your app
is not on port 80, don't forget to put the port in the URL (example: http://techinnovator.online:3000)

Use ctrl-c to exit the app.

Next, install ```pm2``` (process manager 2) to run the app and keep it running when the Terminal is closed.

```npm install pm2 -g```

Note: the ```-g``` is needed. It is to specify install globally. But, since ```npm``` is installed in ```.nvm``` in the
home directory (```~```), ```pm2``` is installed there as well. I found that if ```-g``` isn't included ```which pm2```` can't find it.

When ```-g``` is used, the path, as an example, looks like the following after the installation.

```
~/.nvm/versions/node/v16.19.0/bin/pm2
```

Start the node/express app using pm2. The following command assumes the project folder, where *index.js* is located, is the current working directory.

```pm2 start index.js```

Example:

```
[ec2-user@ip-172-31-88-127 staticapp]$ pm2 start index.js
[PM2] Applying action restartProcessId on app [index](ids: [ 0 ])
[PM2] [index](0) ✓
[PM2] Process successfully started
┌─────┬──────────┬─────────────┬─────────┬─────────┬──────────┬────────┬──────┬───────────┬──────────┬──────────┬──────────┬──────────┐
│ id  │ name     │ namespace   │ version │ mode    │ pid      │ uptime │ ↺    │ status    │ cpu      │ mem      │ user     │ watching │
├─────┼──────────┼─────────────┼─────────┼─────────┼──────────┼────────┼──────┼───────────┼──────────┼──────────┼──────────┼──────────┤
│ 0   │ index    │ default     │ 1.0.0   │ fork    │ 7446     │ 0s     │ 15   │ online    │ 0%       │ 14.4mb   │ ec2-user │ disabled │
└─────┴──────────┴─────────────┴─────────┴─────────┴──────────┴────────┴──────┴───────────┴──────────┴──────────┴──────────┴──────────┘
[ec2-user@ip-172-31-88-127 staticapp]$ 

```

After pm2 starts the node/express app the command prompt returns. The Terminal may now be closed and the app will continue to run.

Test that the node/express server is running and works by going to its URL. Remember to put http:// before the domain name if the app is running on port 80.
 



