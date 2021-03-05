---
title: Things to do for every version of Ubuntu
created: 2017-05-03T01:36:19+05:30
author: ashishdoneriya
description: Configurations that we have to do for each and every version of Ubuntu.
permalink: /things-to-do-ubuntu.html
categories:
  - ubuntu
tags:
  - linux
  - Ubuntu
updated: 2017-05-03T01:36:19+05:30
---

### Update system
```bash
sudo apt-get update && sudo apt-get upgrade
```

### Remove unnecessary apps
```bash
sudo apt-get remove --purge aisleriot gnome-mahjongg deja-dup deja-dup-backend-gvfs totem totem-common totem-mozilla totem-plugins activity-log-manager activity-log-manager-control-center brasero brasero-cdrkit brasero-common  landscape-client-ui-install unity-control-center unity-control-center-signon empathy empathy-common thunderbird thunderbird-gnome-support onboard onboard-data gnome-orca unity-webapps-common shotwell rhythmbox evolution-data-server evolution-data-server-online-accounts gnome-calendar gucharmap cheese vino gnome-mines gnome-sudoku xdiagnose usb-creator-gtk remmina* remmina-common* remmina-plugin-rdp* remmina-plugin-vnc*
```

```bash
sudo apt-get remove $(dpkg --get-selections | cut -f1 | grep -P "^unity-(lens|scope)-" | grep -vP "unity-(lens|scope)-(home|applications|files)" | tr "\n" " ")
```

```bash
sudo apt-get autoremove
```

### Execute sudo without Password
Open terminal and execute command

```bash
sudo visudo
```

Add the below line at the bottom

```bash
username ALL=(ALL) NOPASSWD: ALL
```

Replace username with the username of your system. Now press `Ctrl + X` then `Ctrl + Y` and then press Enter.

### Display full list of startup applications and processes
```bash
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop
```

Now you can open Startup Applications and remove unnecessary applications that starts as ubuntu starts.

### [Enable passwordless ssh](/passwordless-ssh-ubuntu-linux.html)
### [Add noatime to fstab](http://www.pontikis.net/blog/tweak-ssd-ubuntu-16.04)
disable last accessed time.
