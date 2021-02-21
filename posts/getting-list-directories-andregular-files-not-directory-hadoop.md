---
title: How to get the list of only files and not directories in hadoop
created: 2016-09-22T20:16:01+05:30
author: avdheshbansal
description: Get the list of only directories and regular files (which are not directory) in hadoop hdfs data storage
permalink: /getting-list-directories-andregular-files-not-directory-hadoop.html
updated: 2020-03-23T23:17:00+05:30
categories:
  - big-data
tags:
  - Hadoop
---
Guide to get the list of only files and not directories from hdfs data storage  
Logic : hdfs output | linux (ubuntu/centos) commands to get the desired results

Differentiator:  
1- Hadoop returns the output of the ls command in a 8 column form  
2- Directories versus regular files can be identified using the first column of the o/p  
3- In the o/p the directories starts with d and then the permissions of the directory  
4- In the o/p the regular files starts with a -

Following command is to list only regular files in hdfs :

```bash
hadoop fs -ls -R &lt;source_directory&gt; | sed 's/  */ /g' | cut -d\  -f &lt;number_of_column_from_op&gt; --output-delimiter=&lt;output_to_delimit&gt; | grep ^- | cut -d, -f&lt;number_of_column_from_op&gt;
```


Example :

```bash
hadoop fs -ls -R /tmp | sed 's/  */ /g' | cut -d\  -f 1,8 --output-delimiter=',' | grep ^- | cut -d, -f2
```


Following command is to list only directories in hdfs :

```bash
hadoop fs -ls -R &lt;source_directory&gt; | sed 's/  */ /g' | cut -d\  -f &lt;number_of_column_from_op&gt; --output-delimiter=',' | grep ^d | cut -d, -f&lt;number_of_column_from_op&gt;
```


Example :

```bash
hadoop fs -ls -R &lt;source_directory&gt; | sed 's/  */ /g' | cut -d\  -f 1,8 --output-delimiter=',' | grep ^d | cut -d, -f2
```


Efficiently using the cut command : <a href="http://www.folkstalk.com/2012/02/cut-command-in-unix-linux-examples.html" target="_blank" rel="no-follow noopener noreferrer">http://www.folkstalk.com/2012/02/cut-command-in-unix-linux-examples.html</a>  
& sed command : <a href="https://www.tutorialspoint.com/unix/unix-regular-expressions.htm" target="_blank" rel="no-follow noopener noreferrer">https://www.tutorialspoint.com/unix/unix-regular-expressions.htm</a>
