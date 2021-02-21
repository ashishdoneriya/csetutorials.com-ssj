---
title: My Ubuntu Notes
created: 2017-05-03T00:56:57+05:30
updated: 2020-02-28T18:53:00+05:30
author: ashishdoneriya
permalink: /my-ubuntu-notes
---
1. During Installation, always create swap space and a separate partition for the Home directory. Always select that partition for other Linux distributions also but **do not format it**. And create separate users for different-different distributions like /home/ubuntu for Ubuntu, /home/arch for arch Linux and so on.

2. If your system has SSD then donot create swap space from SSD.

3. Use <a href="https://repogen.simplylinux.ch/" target="_blank" rel="nofollow noopener noreferrer">Ubuntu Source List generator</a>.

4. **Run sudo command without password**  
If you don&#8217;t want to type sudo password again and again then run command `sudo visudo` and append the below line at the end.

<pre class="language-bash"><code>your_username ALL=(ALL) NOPASSWD: ALL</code></pre>

Save using `Ctrl + X` and `Shift + y` and press Enter. That&#8217;s it.

5. **Create user from Command line**

<pre>useradd --create-home --system --shell /bin/bash --user-group your_username</pre>

6. XUbuntu is the best Linux distribution (in terms of performance). It has the power to give a new fresh life to slow and dying old pcs.

7. To Generate subtitles of audio and video  
Install

<pre>sudo apt-get install ffmpeg && sudo pip install autosub</pre>

To generate subtitle :

<pre>autosub -o subtitlefile.srt "/path/to/file.mp4 or .mp3"</pre>

If you are using Vlc to play the .mp3 file, then you have to select a visualization (Menu > Audio > Visualization > Select any) because Vlc cannot display subtitles without it.

8. Detach a Linux Processes From Controlling Terminal

<pre>command &lt;/dev/null &&gt;/dev/null &</pre>

9. For setting the paths, the file is /etc/environment

10. <a href="https://devanswers.co/how-to-reset-mysql-root-password-ubuntu/" rel="noopener noreferrer" target="_blank">Reset Mysql Password</a>
