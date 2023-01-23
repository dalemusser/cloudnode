# Create DNS Record

This document describes creating a DNS record to associate the IP address to a domain name.

---
*Assumptions:* this documentation uses DNS management on namecheap.com. It is assumed you have an account with namecheap, are logged in, and 
have a registered domain name to use.

Go to: [namecheap.com](https://www.namecheap.com/)

Click on *Dashboard* from menu on left side of page.

Click on the *MANAGE* button for the domain name in the list of domain names.

On the *Domains -> Details* page for the domain name, click the *Advanced DNS* tab.

The record to be added is an "A Record". Before we do that, consider the following. 

If your domain name is already being used with some other server hosting there will already be a record or records there. It is likely 
the base domain name is assigned to an IP address for a server if there is already hosting. The *Host* for the base domain name 
(dalemusser.com for example) in the host records is an @ and the *Value* is the IP address (165.22.162.195 for example). If you already 
have hosting you don't want to mess this record up. To be sure you can put anything back you delete or change, take a screen capture of 
the info so you have a copy to refer to.

If your domain name is new and not associated with some server, then there are likely records there to provide a placeholder page.
The trash can icon next to a record can be used to delete it. I would delete all the records in the *HOST RECORDS* section if this is
a new domain not yet being used for anything.

To create the "A Record" to associate the domain name with the IP address do the following:

* click *ADD NEW RECORD* below the list of records.
* select "A Record" from the list that pops up.
* in the *Host* field enter:
  * @ if you are using the base domain name (dalemusser.com for example)
  * use the subdomain name if you want a subdomain of the base domain name (nodeapp for nodeapp.dalemusser.com) 
  * set the *Value* to the IP address
  * set TTL to Automatic
* click the green checkbox at the right end of the record to create it

Once you have the DNS record set up and the information has propogated, you can either use the domain name or the IP address when you ssh or use a web 
browser to connect to the server.

After creating it, the record is available to the domain name server. It may, though, take time for the record to be generally available.
If you change DNS records, the changes may take time to propogate and the browser may cache a previous lookup. So, if a domain name is not being
directed to the IP address correctly it may take more time or you may way to clear the browser and restart it.

You can use the ```dig <domain-name>``` at the command line to see what DNS records are associated with a domain. In the following, *dalemusser.com*
has an "A Record" associating it with the IP address of 165.22.162.195.

```
musserda@CEDUC-PT4N2J09RL ~ % dig dalemusser.com

; <<>> DiG 9.10.6 <<>> dalemusser.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 48238
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;dalemusser.com.			IN	A

;; ANSWER SECTION:
dalemusser.com.		1034	IN	A	165.22.162.195

;; Query time: 89 msec
;; SERVER: 75.75.75.75#53(75.75.75.75)
;; WHEN: Sun Jan 22 16:38:40 PST 2023
;; MSG SIZE  rcvd: 59

```

<https://dalemusser.com>
<https://165.22.162.195>


