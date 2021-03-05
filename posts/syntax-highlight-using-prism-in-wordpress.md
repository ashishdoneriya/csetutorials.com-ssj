---
title: Syntax Highlight using Prism in WordPress
created: 2016-07-20T15:47:04+05:30
author: ashishdoneriya
description: Prism is a lightweight, extensible, fast and simple highlighter. It is also used by some famous and popular websites like Mozilla, SitePoint and Drupal. It also provides a lot of extensions also like line highlight, line numbers, autolinker, show language etc.
permalink: /syntax-highlight-using-prism-in-wordpress.html
tags:
  - Wordpress
categories:
  - wordpress
updated: 2016-07-20T15:47:04+05:30
---

[Prism](http://prismjs.com/index.html) is a lightweight, extensible, fast and simple highlighter. It is also used by some famous and popular websites like Mozilla, SitePoint and Drupal. Our website is also using Prism js for syntax highlighting.

Without a syntax highlighter our code look like

```
File file = new File("/home/ashish/error.txt");
FileReader is = new FileReader(file);
		
BufferedReader br = new BufferedReader(is);
String line;
String result = "";
while ( (line = br.readLine()) != null) {
	result += line + '\n';
}
br.close();
return result.split("\n");
```

But with prism syntax highlighter

```java
File file = new File("/home/ashish/error.txt");
FileReader is = new FileReader(file);
		
BufferedReader br = new BufferedReader(is);
String line;
String result = "";
while ( (line = br.readLine()) != null) {
	result += line + '\n';
}
br.close();
return result.split("\n");
```


There are 7 themes available in Prism ([Default](http://prismjs.com/index.html?theme=prism), [Dark](http://prismjs.com/index.html?theme=prism-dark), [Funky](http://prismjs.com/index.html?theme=prism-funky), [Okaidia](http://prismjs.com/index.html?theme=prism-okaidia, [Twilight](http://prismjs.com/index.html?theme=prism-twilight), [Coy](http://prismjs.com/index.html?theme=prism-coy) and [Solarized Light](http://prismjs.com/index.html?theme=prism-solarizedlight)). It supports a wide variety of languages (mostly all of languages you ever heard of). It also provides a lot of extensions also like line highlight, line numbers, autolinker, show language etc.

So lets start

1. Go the [download page](http://prismjs.com/download.html) of Prism.

2. Select your theme. I wiil prefer 'Coy' theme.
[<img loading="lazy" src="/wp-content/uploads/2016/07/highlight-syntex-using-prism.png" alt="highlight syntax using prism" width="1830" height="955" class="aligncenter size-full wp-image-311" srcset="/wp-content/uploads/2016/07/highlight-syntex-using-prism.png 1830w, /wp-content/uploads/2016/07/highlight-syntex-using-prism-500x261.png 500w, /wp-content/uploads/2016/07/highlight-syntex-using-prism-1024x534.png 1024w, /wp-content/uploads/2016/07/highlight-syntex-using-prism-982x512.png 982w, /wp-content/uploads/2016/07/highlight-syntex-using-prism-400x209.png 400w" sizes="(max-width: 1830px) 100vw, 1830px" />](/wp-content/uploads/2016/07/highlight-syntex-using-prism.png)

3. Select the languages that you want to highlight in your website. 
  **Note :** Do not select all languages as the size of javascript file (that prism will generate for you to download) will be increased.
  
4. Select plugins. Plugins add some extra things to your code like adding displaying line numbers, showing highlighted language in top right corner of that code, preview color when hover on css color code and so on. My favourite plugin is 'Line Numbers' plugin.
5. Goto the bottom of the page and download JS and CSS files.  
  [<img loading="lazy" src="/wp-content/uploads/2016/07/prism-download.png" alt="prism donwload" width="941" height="444" class="aligncenter size-full wp-image-315" srcset="/wp-content/uploads/2016/07/prism-download.png 941w, /wp-content/uploads/2016/07/prism-download-500x236.png 500w, /wp-content/uploads/2016/07/prism-download-400x189.png 400w" sizes="(max-width: 941px) 100vw, 941px" />](/wp-content/uploads/2016/07/prism-download.png)
6. Install plugin [Prism Syntax Highlighter for WordPress](https://wordpress.org/plugins/prism/).
7. Goto `Plugins > Editor`. Select 'Prism Syntax Highlighter for WordPress' plugin to edit.
8. In the right side, under 'Plugin Files', open file `prism/prism.css` and replace its content with the contents of the css file that you downloaded from prism.
9. Repeat the same process form `prism/prism.js` file, ie. replace its content with the js file that you downloaded from prism.
10. That it.

Now if you have to beautify any code append the class. eg.
  
```
<pre><code class="language-bash line-numbers">ls
echo 'export PATH=$PATH:/home/username/nodejs/bin' >> /home/username/.bashrc</code></pre>
```
  Output will be
  
```bash
ls
echo 'export PATH=$PATH:/home/username/nodejs/bin' >> /home/username/.bashrc
```
