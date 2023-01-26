# AWS Lightsail Unity WebGL Hosting

This document describes creating and using a Lightsail instance to host a Unity WebGL application.

## Create Instance

Platform: Linux/Unix

Select a blueprint: App + OS, Node.js (16.18.1-10) 
Note: this blueprint comes with Apache installed and running.

Choose your instance plan: $10/month - Memory: 2 GB, Processing: 1 vCPU, Storage: 60 GB SSD, Transfer: 3 TB

Identify your instance: Unity-webGL-Hosting1

## Assigning Public Static IP Address

Go to the Lightsail dashboard and select *Networking*.

Create a static IP address and attach to the instance.

If a static IP address already exists, attach it to the instance.

## Assign Instance to Load Balancer

If there is a load balancer, set the target instance of the load balancer to the Unity-webGL-Hosting1 instance and attach.

## Configure Server Instance

The chosen blueprint already has Apache installed and running.  

The folders for apache configuration and hosting files are located in:

```/opt/bitnami/apache2```

The hosted files go in:

```/opt/bitnami/apache2/htdocs```

Edit the ```http.conf``` file at ```/opt/bitnami/apache2/conf/httpd.conf``` and change the ```AllowOverride None``` to ```AllowOverride All``` in the ```<Directory "/opt/bitnami/apache/htdocs">``` block to allow directives in the ```.htaccess``` file in the hosting directory. The block is shown edited below.

```
DocumentRoot "/opt/bitnami/apache/htdocs"
<Directory "/opt/bitnami/apache/htdocs">
    #
    # Possible values for the Options directive are "None", "All",
    # or any combination of:
    #   Indexes Includes FollowSymLinks SymLinksifOwnerMatch ExecCGI MultiViews
    #
    # Note that "MultiViews" must be named *explicitly* --- "Options All"
    # doesn't give it to you.
    #
    # The Options directive is both complicated and important.  Please see
    # http://httpd.apache.org/docs/2.4/mod/core.html#options
    # for more information.
    #
    Options Indexes FollowSymLinks

    #
    # AllowOverride controls what directives may be placed in .htaccess files.
    # It can be "All", "None", or any combination of the keywords:
    #   AllowOverride FileInfo AuthConfig Limit
    #
    AllowOverride All 

    #
    # Controls who can get stuff from this server.
    #
    Require all granted
</Directory>
```

Restart apache so it will use the change to the conf.

```sudo /opt/bitnami/ctlscript.sh restart apache```

Create an ```.htaccess``` file in ```/opt/bitnami/apache2/htdocs``` that contains the following.

The following is from [Server configuration code samples (Unity)](https://docs.unity3d.com/2023.1/Documentation/Manual/webgl-server-configuration-code-samples.html). I used this as provided except the ```application/wasm``` line was changed to ```AddType application/wasm .wasm .wasm.gz```. 

```
<IfModule mod_mime.c>
RemoveType .gz
AddEncoding gzip .gz
# The correct MIME type for .data.gz would be application/octet-stream, but due to Safari bug https://bugs.webkit.org/show_bug.cgi?id=247421, it is preferable to use MIME Type application/gzip instead.
#AddType application/octet-stream .data.gz
AddType application/gzip .data.gz
AddType application/wasm .wasm .wasm.gz
AddType application/javascript .js.gz
AddType application/octet-stream .symbols.json.gz

RemoveType .br
AddEncoding br .br
AddType application/octet-stream .data.br
AddType application/wasm .wasm.br
AddType application/javascript .js.br
AddType application/octet-stream .symbols.json.br

</IfModule>
```

Remove or rename the existing ```index.html``` in ```/opt/bitnami/apache2/htdocs```.

```mv index.html index.html.orig```

Copy Unity WebGL application to ```/opt/bitnami/apache2/htdocs```.
Note: zip app and scp to home directory. Copy zip to ```htdocs``` and ```unzip```.


