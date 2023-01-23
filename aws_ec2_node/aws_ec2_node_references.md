Information on setting up a cloud server and running a node/express js app.

<https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/setting-up-node-on-ec2-instance.html><br />
<https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EC2_GetStarted.html><br />
<https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/get-set-up-for-amazon-ec2.html>

<https://ourcodeworld.com/articles/read/977/how-to-deploy-a-node-js-application-on-aws-ec2-server>
<https://docs.npmjs.com/downloading-and-installing-node-js-and-npm>

```
musserda@CEDUC-PT4N2J09RL cloudnode % scp -i "Dale Musser AWS1.pem" staticapp.zip ec2-user@techinnovator.online:
staticapp.zip                                                        100%  779KB   1.3MB/s   00:00    
musserda@CEDUC-PT4N2J09RL cloudnode % 

```
<https://stackoverflow.com/questions/60372618/nodejs-listen-eacces-permission-denied-0-0-0-080>
<https://expressjs.com/en/starter/static-files.html>

<https://stackoverflow.com/questions/55414302/an-ip-address-of-ec2-instance-gets-changed-after-the-restart#:~:text=Actually%2C%20When%20you%20stop%2Fstart,used%20by%20other%20EC2%20instances.>
<https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html#eip-pricing>
<https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html>

```
scp -i "Dale Musser AWS1.pem" staticapp.zip ec2-user@techinnovator.online:
```
```
ssh -i "Dale Musser AWS1.pem" ec2-user@techinnovator.online
```
<https://pm2.keymetrics.io/docs/usage/process-management/>
<https://expressjs.com/en/starter/static-files.html>
<https://www.digitalocean.com/community/tutorials/nodejs-serving-static-files-in-express>
<https://stackoverflow.com/questions/5924072/express-js-cant-get-my-static-files-why>

<https://technoapple.com/blog/post/How-to-Setup-a-HTTPS-Node-JS-Server-on-Amazon-EC2>
<https://dev.to/arifintahu/how-to-set-up-free-ssl-for-nodejs-app-in-aws-ec2-30fj>
<https://stackoverflow.com/questions/36774492/running-a-simple-https-node-js-server-on-amazon-ec2>
<https://stackoverflow.com/questions/47159315/enable-https-on-node-express-app-on-aws-ec2>
<https://www.cronj.com/blog/https-node-js-aws-ec2-node-js/>
