---
title: How to use Eslint in Sublime
created: 2016-05-20T18:56:55+05:30
author: ashishdoneriya
permalink: /how-to-use-eslint.html
categories:
  - web-development
tags:
  - sublime
updated: 2016-05-20T18:56:55+05:30
---
Steps to use Esline in Sublime code editor.

1. Install nodejs and npm in system.
2. Install eslint using command 
```bash
sudo npm install -g eslint
```


3. Create package.json file using command 
```bash
npm init
```


Fill anything you want

* Create config file for eslint using 
```bash
eslint --init
```

Answer the questions that it will ask

* Open sublime and install package `Eslint Formattor`. Goto  `Preferences > Package Settings > ESLintFormatter > Settings - User`.  
Set proper path of `eslint_path`. You can get the path using `whereis eslint`. Now set `config_path` as `/home/username/.eslintrc.js`. Change username.
* That's all

Now to format using eslint Right click and Select Eslint Formatter > Format this file.
