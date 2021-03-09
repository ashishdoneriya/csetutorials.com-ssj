---
title: How to setup Kerberos on Ubuntu
created: 2017-07-05T19:58:34+05:30
author: ashishdoneriya
description: Steps to setup Kerberos server, administrative server and Kerberos client on Ubuntu Linux and also setup Kerberos authentication
permalink: /setup-kerberos-ubuntu.html
tags:
  - kerberos
  - Ubuntu
updated: 2017-07-05T19:58:34+05:30
categories:
  - ubuntu
---
In a network, there is one machine which acts as a server for Kerberos authentication and rest of the machines act as clients. On the server machine, we will install Kerberos administrative server and database for Kerberos. On client machines, we will install Kerberos client. So first we will setup Kerberos server.

## Setting Kerberos Server

Execute the below command to install Kerberos admin server and KDE (key distribution center).

```bash
sudo apt install krb5-kdc krb5-admin-server
```


It will ask you the following three things one by one  
1. Kerberos realm. (let's say MYREALM)  
2. Kerberos server hostname. Type `localhost` and enter.  
3. Hostname of the administrative (password changing) server for MYREALM. In this case type `localhost` and enter.  
[<img loading="lazy" width="1858" height="1054" src="/wp-content/uploads/2017/07/kerberos-installation-1.png" alt="Kerberos installation" class="aligncenter size-full wp-image-827" srcset="/wp-content/uploads/2017/07/kerberos-installation-1.png 1858w, /wp-content/uploads/2017/07/kerberos-installation-1-500x284.png 500w, /wp-content/uploads/2017/07/kerberos-installation-1-1024x581.png 1024w, /wp-content/uploads/2017/07/kerberos-installation-1-982x557.png 982w, /wp-content/uploads/2017/07/kerberos-installation-1-400x227.png 400w" sizes="(max-width: 1858px) 100vw, 1858px" />](/wp-content/uploads/2017/07/kerberos-installation-1.png)  
[<img loading="lazy" width="1856" height="1054" src="/wp-content/uploads/2017/07/kerberos-installation-2.png" alt="kerberos installation" class="aligncenter size-full wp-image-828" srcset="/wp-content/uploads/2017/07/kerberos-installation-2.png 1856w, /wp-content/uploads/2017/07/kerberos-installation-2-500x284.png 500w, /wp-content/uploads/2017/07/kerberos-installation-2-1024x582.png 1024w, /wp-content/uploads/2017/07/kerberos-installation-2-982x558.png 982w, /wp-content/uploads/2017/07/kerberos-installation-2-400x227.png 400w" sizes="(max-width: 1856px) 100vw, 1856px" />](/wp-content/uploads/2017/07/kerberos-installation-2.png)  
[<img loading="lazy" width="1855" height="1054" src="/wp-content/uploads/2017/07/kerberos-installation-3.png" alt="kerberos installation" class="aligncenter size-full wp-image-829" srcset="/wp-content/uploads/2017/07/kerberos-installation-3.png 1855w, /wp-content/uploads/2017/07/kerberos-installation-3-500x284.png 500w, /wp-content/uploads/2017/07/kerberos-installation-3-1024x582.png 1024w, /wp-content/uploads/2017/07/kerberos-installation-3-982x558.png 982w, /wp-content/uploads/2017/07/kerberos-installation-3-400x227.png 400w" sizes="(max-width: 1855px) 100vw, 1855px" />](/wp-content/uploads/2017/07/kerberos-installation-3.png)  
[<img loading="lazy" width="1860" height="1060" src="/wp-content/uploads/2017/07/kerberos-installation-4.png" alt="kerberos installation" class="aligncenter size-full wp-image-830" srcset="/wp-content/uploads/2017/07/kerberos-installation-4.png 1860w, /wp-content/uploads/2017/07/kerberos-installation-4-500x285.png 500w, /wp-content/uploads/2017/07/kerberos-installation-4-1024x584.png 1024w, /wp-content/uploads/2017/07/kerberos-installation-4-982x560.png 982w, /wp-content/uploads/2017/07/kerberos-installation-4-400x228.png 400w" sizes="(max-width: 1860px) 100vw, 1860px" />](/wp-content/uploads/2017/07/kerberos-installation-4.png)

Now execute the below command to setup realm.

```bash
sudo krb5_newrealm
```


It will ask you to enter a password for database creation and after that, it will start Kerberos KDC krb5kdc and Kerberos administrative servers kadmind processes.

Open `/etc/krb5kdc/kadm5.acl` file with your favourite text editor and uncomment the last line so that the file would look like.

```bash
# This file Is the access control list for krb5 administration.
# When this file is edited run /etc/init.d/krb5-admin-server restart to activate
# One common way to set up Kerberos administration is to allow any principal
# ending in /admin  is given full administrative rights.
# To enable this, uncomment the following line:
*/admin *
```

Your Kerberos server has been setup.

If you want to add principal, execute

```bash
sudo kadmin.local
```


and then run the command `addprinc` inside `kadmin.local`

```bash
addprinc your_principal_name
```

eg.

```bash
addprinc ashishdoneriya
```

## Setting Kerberos Client

Add Kerberos server machine entry in your client machine /etc/hosts file. Let's say the hostname of the machine in which you have just installed Kerberos server is 'host1' and IP is '192.168.1.10' then add this line to /etc/hosts 

```bash
192.168.1.10    host1
```

Execute the below command to install and setup Kerberos client.

```bash
sudo apt-get install krb5-user
```


It will ask 3 thing one by one  
realm - MYREALM  
hostname - host1  
admin server - host1

That's it. Now to test, run command

```bash
kinit -p your_principal_name@MYREALM
```


eg. 

```bash
kinit -p ashishdoneriya@MYREALM
```

If you want to remove kerberos and all its configuration and pacakages from your system then

```bash
sudo apt-get remove --purge krb5-admin-server krb5-config krb5-kdc krb5-locales
```

**Update :** Once I had to setup kerberos client on my machine and the kdc is MIT kdc. Then I setup client on my machine using above process. After that I was facing problems in java during authentication and authorization using kerberos. After a lot of debugging, I found that in my system, encryption types in file `/etc/krb5.conf` is different than kerberos server's `/etc/krb5.conf`. So I replaced my system's `/etc/krb5.conf` with server's and then my java code worked fine.

Sources:  
[https://help.ubuntu.com/community/Kerberos](https://help.ubuntu.com/community/Kerberos)
[https://help.ubuntu.com/lts/serverguide/kerberos.html](https://help.ubuntu.com/lts/serverguide/kerberos.html)
