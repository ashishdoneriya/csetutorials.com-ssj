---
title: How to setup Jumbune
created: 2017-03-31T22:01:30+05:30
author: ashishdoneriya
description: Instructions to setup jumbune enterprise on your machine / cluster
permalink: /how-to-setup-jumbune.html
updated: 2020-03-16T14:24:00+05:30
categories:
  - big-data
tags:
  - Hadoop
  - jumbune
---

First download the jar from [Jumbune website](http://www.jumbune.com/) and get the licence.

In your system you have to set some environment variable.

  * `JAVA_HOME`
  * `HADOOP_HOME`
  * `JUMBUNE_HOME` : Path of directory in which you want to install jumbune (eg. '/home/ashish/jumbune'). It contains all jars and settings of jumbune.
  * `HADOOP_HOME` eg. '/home/ashish/jumbune-agent'

Now run the setup jar

```bash
java -jar jumbune-ee-dist-1.0-bin.jar
```


It will ask you following questions :

```bash
Choose the Hadoop Distribution Type : (a)Apache | (c)Cloudera | (e)EMR | (h)HortonWorks | (m)MapR
```


Select the hadoop distribution Type

```bash
IP address of the namenode machine [192.168.1.2]
```


Type the IP address of namenode machine and press enter. If you just press enter then it will assume the displayed (eg. 192.168.1.2) ip address.

```bash
Username of the namenode machine: [ashish]
```


```bash
Do we have passwordless SSH between [192.168.1.2] - [192.168.1.8] machines? (y)/(n)
```


If you have passwordless ssh between namenode machine and the machine in which you are installing jumbune then enter 'y' otherwise 'n'. If you enter 'n' then in the next step you were asked to enter password of namenode machine.

```bash
Password of the namenode machine:
```


Then it will display some output/ lines

```bash
Establishing session between [192.168.1.2] - [192.168.1.8] machines.......[SUCCESS]
Extracting Jumbune...
Using Hadoop: [/home/ashish/hadoop/]
Jumbune Extraction, Directories creation, Configuration update.......[SUCCESS]
Using Hadoop: [/home/ashish/hadoop/]
scp: /home/ashish/hadoop/share/hadoop/common/lib/htrace-core*.jar: No such file or directory

Syncing Jars from Hadoop to Jumbune.......[SUCCESS]
```


Jumbune requires influx database for some of its features to make work.

So it will ask you the question

```bash
Influxdb is required for persistence of Cluster Analysis stats.
(i) Install & Configure InfluxDB | (c) Just Configure InfluxDB | (l) Install Later
```


If you want jumbune to automatic install and configure influxdb then enter 'i'. If you have influxdb already installed in your machine then enter 'c'. If you want to install influxdb later then enter 'l'. Follow the instructions after that. You could also install and configure influxdb after installation of jumbune by execution script (`$JUMBUNE_HOME/bin/install-influxdb.sh`).

## To run jumbune

To run jumbune, you have to run two things.  
1. Jumbune container  
2. Jumbune Agent (.jar file)

You have to run jumbune agent on namenode machine, and jumbune container from the machine in which you have just installed jumbune.

### To run Jumbune Agent

Create a directory called `jumbune-agent` in your namenode machine.  
Copy the directory agent-distribution (which is install Jumbune home) to your namenode machine (in `jumbune-agent`)( eg. /home/ashish/jumbune-agent/agent-distribution).

In namenode machine open the script file `jumbune-agent/agent-distribution/bin/startAgent` and change the parameters according to your need.  
eg. If you have high availability enabled then uncomment the `HA` option and provide the values.  
If you have zookeeper installed then uncomment and fill `ZK_OPTION`.  
By default jumbune will start its agent at port 2161. If you want to change port then modify `AGENT_PORT` variable.

Save the `startAgent` script and execute it from terminal. You need to first make the script executable.

```java
ashish@pc:~$chmod +x startAgent
ashish@pc:~$./startAgent

[sudo] password for ashish: 
Choose the Hadoop Distribution Type : (a)Apache | (c)Cloudera | (e)EMR | (h)HortonWorks | (m)MapR
a
Please verify Hadoop installation directory [/home/ashish/hadoop/hadoop/]

Jumbune Agent started successfully on port [2161]
164 [nioEventLoopGroup-2-1] INFO io.netty.handler.logging.LoggingHandler - [id: 0x05fe7262] REGISTERED
165 [nioEventLoopGroup-2-1] INFO io.netty.handler.logging.LoggingHandler - [id: 0x05fe7262] BIND(0.0.0.0/0.0.0.0:2161)
167 [nioEventLoopGroup-2-1] INFO io.netty.handler.logging.LoggingHandler - [id: 0x05fe7262, /0:0:0:0:0:0:0:0:2161] ACTIVE

```


The agent is up and running now.

### To run Jumbune Container

Goto to the machine in which you have just installed jumbune and start the script startWeb ($JUMBUNE_HOME/bin/startWeb).

```bash
ashish@pc:~$ JUMBUNE_HOME/bin/startWeb	

JUMBUNE : INFO : JAVA HOME path : /opt/jdk1.7.0_79
JUMBUNE : INFO : HADOOP HOME path : /home/ashish/hadoop/hadoop/
JUMBUNE : INFO : JUMBUNE HOME path : /home/ashish/jumbunehome/
2017-03-31 22:22:08.264:INFO::main: Logging initialized @70ms
2017-03-31 22:22:08.280:INFO:oejr.Runner:main: Runner
2017-03-31 22:22:08.375:INFO:oejs.Server:main: jetty-9.2.11.v20150529
2017-03-31T22:22:13,068 INFO  [main][EventLogger] Dear Jumbune Member! Your Jumbune subscription license will expire in [38] day(s)
2017-03-31 22:22:14.102:INFO:oejsh.ContextHandler:main: Started o.e.j.w.WebAppContext@1578fd24{/,file:/home/ashish/jumbunehome/modules/jumbune-web-1.0/,AVAILABLE}{file:/home/ashish/jumbunehome/modules/jumbune-web-1.0.war}
2017-03-31 22:22:14.104:WARN:oejsh.RequestLogHandler:main: !RequestLog
2017-03-31 22:22:14.109:INFO:oejs.ServerConnector:main: Started ServerConnector@34817d92{HTTP/1.1}{0.0.0.0:8080}
2017-03-31 22:22:14.110:INFO:oejs.Server:main: Started @5918ms

```


Thats it.

It will start jumbune container at port 8080. Now open your browser and hit address `localhost:8080`

<div id="attachment_628" style="width: 1862px" class="wp-caption aligncenter">
  <a href="/wp-content/uploads/2017/03/jumbune-home.png"><img aria-describedby="caption-attachment-628" loading="lazy" class="size-full wp-image-628" src="/wp-content/uploads/2017/03/jumbune-home.png" alt="Jumbune Home Page" width="1852" height="963" srcset="/wp-content/uploads/2017/03/jumbune-home.png 1852w, /wp-content/uploads/2017/03/jumbune-home-500x260.png 500w, /wp-content/uploads/2017/03/jumbune-home-1024x532.png 1024w, /wp-content/uploads/2017/03/jumbune-home-982x511.png 982w, /wp-content/uploads/2017/03/jumbune-home-400x208.png 400w" sizes="(max-width: 1852px) 100vw, 1852px" /></a>
  
  <p id="caption-attachment-628" class="wp-caption-text">
    Jumbune Home Page
  </p>
</div>
