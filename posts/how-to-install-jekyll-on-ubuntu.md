---
title: How to install Jekyll on Ubuntu without any error
created: 2018-10-12T00:22:04+05:30
author: ashishdoneriya
description: Install Jekyll successfully on Ubuntu without any error
permalink: /how-to-install-jekyll-on-ubuntu.html
updated: 2020-03-04T02:00:00+05:30
tags:
  - Jekyll
  - Ubuntu
categories:
  - web-development
  - ubuntu
---

As you are already aware that Jekyll is a static site generator. But when you will start using it, then you will know how awesome and powerful it is. If you want to start a blog without paying any hosting fees then I recommend you to use Jekyll + Github combination. In this guide I am going to tell you how to install Jekyll on Ubuntu successfully unlike the steps mentioned on official Jekyll site that do not work.

## Steps to install Jekyll

1. Install Ruby

```bash
sudo apt-get install ruby ruby-dev build-essential
```


2. Add Environment variable to `~/.bashrc` field

```bash
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME=$HOME/gems' >> ~/.bashrc
echo 'export PATH=$HOME/gems/bin:$PATH' >> ~/.bashrc
source ~/.bashrc
```


3. Now comes the tricky part. According to the official documentation, it says you can install Jekyll by executing the below common

```bash
gem install jekyll bundler
```


The above command didn't work for me. I got an error saying

```
bash: /usr/local/bin/gem: /usr/local/bin/ruby: bad interpreter: No such file or directory
```


So after some research I found gem binary file is in `/usr/bin` directory. Therefore finally I executed the below command to install Jekyll on my Ubuntu machine.

```bash
/usr/bin/gem install jekyll bundler
```


4. That's it. Now you can resume your <a href="https://jekyllrb.com/docs/step-by-step/01-setup/#create-a-site" target="_blank" rel="nofollow noopener noreferrer">journey to the Jekyll</a>.
