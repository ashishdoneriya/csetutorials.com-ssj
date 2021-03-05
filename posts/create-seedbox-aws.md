---
title: How to create a seedbox using AWS
created: 2019-12-06T00:57:33+05:30
author: ashishdoneriya
description: How to create a seedbox using aws and download torrent files.
permalink: /create-seedbox-aws.html
updated: 2020-03-14T00:04:00+05:30
categories:
  - internet
tags:
  - aws
  - seedbox
---

In this article I'm going to tell you how to create a seedbox using [AWS (Amazon Web Service)](/what-is-amazon-web-services.html). Using seedbox we can download torrent files like Ubuntu disk image etc.

To create a seedbox first I will create a aws lambda instance (virtual machine) and then activate seedbox using [cloud-torrent](https://github.com/jpillora/cloud-torrent). So here are the steps.

**1.** Login to you aws account. If you don't have an aws account then create it and then login. You have to have a credit or debit card for creating an account in aws.

**2. Open Lightsail service.**

[<img loading="lazy" class="aligncenter size-full wp-image-1320" src="/wp-content/uploads/2019/12/aws-lighsail.png" alt="AWS Lightsail" width="1518" height="772" srcset="/wp-content/uploads/2019/12/aws-lighsail.png 1518w, /wp-content/uploads/2019/12/aws-lighsail-500x254.png 500w, /wp-content/uploads/2019/12/aws-lighsail-1024x521.png 1024w, /wp-content/uploads/2019/12/aws-lighsail-982x499.png 982w, /wp-content/uploads/2019/12/aws-lighsail-400x203.png 400w" sizes="(max-width: 1518px) 100vw, 1518px" />](/wp-content/uploads/2019/12/aws-lighsail.png)

**3. Create an instance.**

[<img loading="lazy" class="aligncenter size-full wp-image-1321" src="/wp-content/uploads/2019/12/aws-lightsail-create-instance-button.png" alt="Aws Lightsail Create Instance button" width="1453" height="734" srcset="/wp-content/uploads/2019/12/aws-lightsail-create-instance-button.png 1453w, /wp-content/uploads/2019/12/aws-lightsail-create-instance-button-500x253.png 500w, /wp-content/uploads/2019/12/aws-lightsail-create-instance-button-1024x517.png 1024w, /wp-content/uploads/2019/12/aws-lightsail-create-instance-button-982x496.png 982w, /wp-content/uploads/2019/12/aws-lightsail-create-instance-button-400x202.png 400w" sizes="(max-width: 1453px) 100vw, 1453px" />](/wp-content/uploads/2019/12/aws-lightsail-create-instance-button.png)

**4. Under `Select a blueprint` label. Click on `OS Only`.**

[<img loading="lazy" class="aligncenter size-full wp-image-1323" src="/wp-content/uploads/2019/12/aws-lightsail-select-os.png" alt="AWS Lightsail Select OS Only" width="1288" height="722" srcset="/wp-content/uploads/2019/12/aws-lightsail-select-os.png 1288w, /wp-content/uploads/2019/12/aws-lightsail-select-os-500x280.png 500w, /wp-content/uploads/2019/12/aws-lightsail-select-os-1024x574.png 1024w, /wp-content/uploads/2019/12/aws-lightsail-select-os-982x550.png 982w, /wp-content/uploads/2019/12/aws-lightsail-select-os-400x224.png 400w" sizes="(max-width: 1288px) 100vw, 1288px" />](/wp-content/uploads/2019/12/aws-lightsail-select-os.png)

**5. Select Ubuntu 18.04 OS.**

[<img loading="lazy" class="aligncenter size-full wp-image-1324" src="/wp-content/uploads/2019/12/aws-lightsail-select-os-ubuntu.png" alt="AWS Lightsail select Ubuntu 18.04 OS" width="1147" height="740" srcset="/wp-content/uploads/2019/12/aws-lightsail-select-os-ubuntu.png 1147w, /wp-content/uploads/2019/12/aws-lightsail-select-os-ubuntu-500x323.png 500w, /wp-content/uploads/2019/12/aws-lightsail-select-os-ubuntu-1024x661.png 1024w, /wp-content/uploads/2019/12/aws-lightsail-select-os-ubuntu-982x634.png 982w, /wp-content/uploads/2019/12/aws-lightsail-select-os-ubuntu-400x258.png 400w" sizes="(max-width: 1147px) 100vw, 1147px" />](/wp-content/uploads/2019/12/aws-lightsail-select-os-ubuntu.png)

**6. Select instance type**  
[<img loading="lazy" class="aligncenter size-full wp-image-1327" src="/wp-content/uploads/2019/12/aws-lightsail-instance-type.png" alt="Select instance type in Lightsail" width="1252" height="722" srcset="/wp-content/uploads/2019/12/aws-lightsail-instance-type.png 1252w, /wp-content/uploads/2019/12/aws-lightsail-instance-type-500x288.png 500w, /wp-content/uploads/2019/12/aws-lightsail-instance-type-1024x591.png 1024w, /wp-content/uploads/2019/12/aws-lightsail-instance-type-982x566.png 982w, /wp-content/uploads/2019/12/aws-lightsail-instance-type-400x231.png 400w" sizes="(max-width: 1252px) 100vw, 1252px" />](/wp-content/uploads/2019/12/aws-lightsail-instance-type.png)

I would recommend you to select a minimum $5 plan. In $5 plan you have to pla $5 a month for the machine in which you get 1 GB Ram, cpu of 1 core, 40 GB SSD Storage and 1 TB of total data transfer bandwidth.

**7. Now click on create instance button at the end of the page.**  
[<img loading="lazy" class="aligncenter size-full wp-image-1329" src="/wp-content/uploads/2019/12/aws-lightsail-create-instance-button-final.png" alt="AWS Create Instance" width="1338" height="702" srcset="/wp-content/uploads/2019/12/aws-lightsail-create-instance-button-final.png 1338w, /wp-content/uploads/2019/12/aws-lightsail-create-instance-button-final-500x262.png 500w, /wp-content/uploads/2019/12/aws-lightsail-create-instance-button-final-1024x537.png 1024w, /wp-content/uploads/2019/12/aws-lightsail-create-instance-button-final-982x515.png 982w, /wp-content/uploads/2019/12/aws-lightsail-create-instance-button-final-400x210.png 400w" sizes="(max-width: 1338px) 100vw, 1338px" />](/wp-content/uploads/2019/12/aws-lightsail-create-instance-button-final.png)

Your instance (machine) will be up and running in a few minutes.

**8. Now click on the terminal icon.**  
[<img loading="lazy" class="aligncenter size-full wp-image-1333" src="/wp-content/uploads/2019/12/aws-lightsail-terminal-icon.png" alt="" width="1293" height="608" srcset="/wp-content/uploads/2019/12/aws-lightsail-terminal-icon.png 1293w, /wp-content/uploads/2019/12/aws-lightsail-terminal-icon-500x235.png 500w, /wp-content/uploads/2019/12/aws-lightsail-terminal-icon-1024x482.png 1024w, /wp-content/uploads/2019/12/aws-lightsail-terminal-icon-982x462.png 982w, /wp-content/uploads/2019/12/aws-lightsail-terminal-icon-400x188.png 400w" sizes="(max-width: 1293px) 100vw, 1293px" />](/wp-content/uploads/2019/12/aws-lightsail-terminal-icon.png)

This will open a terminal in a new window.

[<img loading="lazy" class="aligncenter size-full wp-image-1336" src="/wp-content/uploads/2019/12/aws-lightsail-terminal.png" alt="" width="1016" height="857" srcset="/wp-content/uploads/2019/12/aws-lightsail-terminal.png 1016w, /wp-content/uploads/2019/12/aws-lightsail-terminal-500x422.png 500w, /wp-content/uploads/2019/12/aws-lightsail-terminal-982x828.png 982w, /wp-content/uploads/2019/12/aws-lightsail-terminal-400x337.png 400w" sizes="(max-width: 1016px) 100vw, 1016px" />](/wp-content/uploads/2019/12/aws-lightsail-terminal.png)

**9. Run the below command in the terminal**

```bash
curl https://i.jpillora.com/cloud-torrent! | sudo bash
```

[<img loading="lazy" class="aligncenter size-full wp-image-1337" src="/wp-content/uploads/2019/12/aws-lightbox-terminal-cloud-torrent-installation.png" alt="" width="1014" height="794" srcset="/wp-content/uploads/2019/12/aws-lightbox-terminal-cloud-torrent-installation.png 1014w, /wp-content/uploads/2019/12/aws-lightbox-terminal-cloud-torrent-installation-500x392.png 500w, /wp-content/uploads/2019/12/aws-lightbox-terminal-cloud-torrent-installation-982x769.png 982w, /wp-content/uploads/2019/12/aws-lightbox-terminal-cloud-torrent-installation-400x313.png 400w" sizes="(max-width: 1014px) 100vw, 1014px" />](/wp-content/uploads/2019/12/aws-lightbox-terminal-cloud-torrent-installation.png)  
This will install cloud-torrent app using which we'll start seedbox.

**10. Execute below command and press enter button 4-5 times and after that close the window (by clicking on the X button in left or right or whatever)**

```bash
nohup sudo cloud-torrent --port 80 &
```

[<img loading="lazy" class="aligncenter size-full wp-image-1340" src="/wp-content/uploads/2019/12/lightsail-turn-on-seedbox.png" alt="" width="1024" height="858" srcset="/wp-content/uploads/2019/12/lightsail-turn-on-seedbox.png 1024w, /wp-content/uploads/2019/12/lightsail-turn-on-seedbox-500x419.png 500w, /wp-content/uploads/2019/12/lightsail-turn-on-seedbox-982x823.png 982w, /wp-content/uploads/2019/12/lightsail-turn-on-seedbox-400x335.png 400w" sizes="(max-width: 1024px) 100vw, 1024px" />](/wp-content/uploads/2019/12/lightsail-turn-on-seedbox.png)

**11. In previous window click on the title Ubuntu-1.**

[<img loading="lazy" class="aligncenter size-full wp-image-1343" src="/wp-content/uploads/2019/12/aws-lambda-1.png" alt="" width="1221" height="645" srcset="/wp-content/uploads/2019/12/aws-lambda-1.png 1221w, /wp-content/uploads/2019/12/aws-lambda-1-500x264.png 500w, /wp-content/uploads/2019/12/aws-lambda-1-1024x541.png 1024w, /wp-content/uploads/2019/12/aws-lambda-1-982x519.png 982w, /wp-content/uploads/2019/12/aws-lambda-1-400x211.png 400w" sizes="(max-width: 1221px) 100vw, 1221px" />](/wp-content/uploads/2019/12/aws-lambda-1.png)

This will openup the details of this machine. Copy this public ip and open it in your browser.

[<img loading="lazy" class="aligncenter size-full wp-image-1351" src="/wp-content/uploads/2019/12/aws-lightsail-public-ip.png" alt="" width="1175" height="686" />](/wp-content/uploads/2019/12/aws-lightsail-public-ip.png)[<img loading="lazy" class="aligncenter size-full wp-image-1353" src="/wp-content/uploads/2019/12/aws-lightsail-public-ip.png" alt="" width="1175" height="686" srcset="/wp-content/uploads/2019/12/aws-lightsail-public-ip.png 1175w, /wp-content/uploads/2019/12/aws-lightsail-public-ip-500x292.png 500w, /wp-content/uploads/2019/12/aws-lightsail-public-ip-1024x598.png 1024w, /wp-content/uploads/2019/12/aws-lightsail-public-ip-982x573.png 982w, /wp-content/uploads/2019/12/aws-lightsail-public-ip-400x234.png 400w" sizes="(max-width: 1175px) 100vw, 1175px" />](/wp-content/uploads/2019/12/aws-lightsail-public-ip.png)

**Your seedbox is ready.**

[<img loading="lazy" class="aligncenter size-full wp-image-1358" src="/wp-content/uploads/2019/12/aws-seedbox-screenshot.png" alt="" width="1287" height="645" srcset="/wp-content/uploads/2019/12/aws-seedbox-screenshot.png 1287w, /wp-content/uploads/2019/12/aws-seedbox-screenshot-500x251.png 500w, /wp-content/uploads/2019/12/aws-seedbox-screenshot-1024x513.png 1024w, /wp-content/uploads/2019/12/aws-seedbox-screenshot-982x492.png 982w, /wp-content/uploads/2019/12/aws-seedbox-screenshot-400x200.png 400w" sizes="(max-width: 1287px) 100vw, 1287px" />](/wp-content/uploads/2019/12/aws-seedbox-screenshot.png)

To delete the instance, first stop the machine, and then delete.

[<img loading="lazy" class="aligncenter size-full wp-image-1349" src="/wp-content/uploads/2019/12/aws-lightsail-delete-machine.png" alt="" width="1220" height="682" srcset="/wp-content/uploads/2019/12/aws-lightsail-delete-machine.png 1220w, /wp-content/uploads/2019/12/aws-lightsail-delete-machine-500x280.png 500w, /wp-content/uploads/2019/12/aws-lightsail-delete-machine-1024x572.png 1024w, /wp-content/uploads/2019/12/aws-lightsail-delete-machine-982x549.png 982w, /wp-content/uploads/2019/12/aws-lightsail-delete-machine-400x224.png 400w" sizes="(max-width: 1220px) 100vw, 1220px" />](/wp-content/uploads/2019/12/aws-lightsail-delete-machine.png)

Here is the video of all steps

<iframe src="https://www.youtube.com/embed/ZhtmSEyPyKg" width="560" height="315" frameborder="0" allowfullscreen="allowfullscreen"></iframe>
