---
title: How to setup Node.js on Ubuntu
created: 2016-07-06T19:18:50+05:30
author: ashishdoneriya
description: install or setup node.js on ubuntu or other linux distribution. nodejs ubuntu
permalink: /setup-node-js-ubuntu.html
categories:
  - web-development
  - ubuntu
tags:
  - Nodejs
  - Ubuntu
updated: 2016-07-06T19:18:50+05:30
---

Steps to install NodeJs ubuntu

1. Download nodejs from [Nodejs](https://nodejs.org/en/) website. 
 ```bash
wget https://nodejs.org/dist/v4.4.7/node-v4.4.7-linux-x64.tar.xz
```


2. Extract the compressed file 
```bash
tar xf node-v4.4.7-linux-x64.tar.xz node-v4.4.7-linux-x64/
```


3. Add nodejs bin path to PATH environment 
```bash
echo '
export PATH=$PATH:/home/username/nodejs/bin' >> /home/username/.bashrc
```


4. That's it

Now to run nodejs just type `nodejs` in your terminal.

You can also install package [yarn](https://www.npmjs.com/package/yarn). It is just like mvn (java). If you have to add any package type yarn add
