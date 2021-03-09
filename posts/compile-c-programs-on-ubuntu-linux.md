---
title: How to write C or C++ programs on Ubuntu Linux
created: 2018-10-01T14:36:49+05:30
author: ashishdoneriya
description: "A beginner's guide to write, compile and run c and c++ programs on ubuntu linux. compile c program linux"
permalink: /compile-c-programs-on-ubuntu-linux.html
categories:
  - ubuntu
  - ide
tags:
  - programming
  - Ubuntu
updated: 2018-10-01T14:36:49+05:30
---

If you are a newbie in the linux world you are the facing the question - how to compile c program in linux or how to compile c++ program in linux. So in this post I'm going to explain the steps using which you can run your c c++ programs on linux.

There are two ways to write and run C and C++ programs on Ubuntu.  
1. Using command line  
2. Using IDE (app)

## Using command line

To run a C or C++ program on linux, there are three phases write code, compile code and run it. First you have to write your code using a text editor eg. gedit (it is just like Notepad++). Then after writing the code you have to manually compile the code using particular commands, the compiler creates an executable file ( just like .exe in windows) for our code and then we run that executable file

For compile C programs you need `gcc` c compiler linux tool which is installed by default on Ubuntu. For running C++ programs you need `g++` tool which is not installed by default on Ubuntu. You have to install it by running command

```bash
sudo apt-get install g++

```

### Running a C program

**NOTE :** `#include<conio.h>` will not work on Ubuntu.

Create a text file named `test.c`  
[<img loading="lazy" src="/wp-content/uploads/2018/10/writing-c-program-on-ubuntu-linux.png" alt="Writing C program" width="1920" height="1080" class="aligncenter size-full wp-image-1098" srcset="/wp-content/uploads/2018/10/writing-c-program-on-ubuntu-linux.png 1920w, /wp-content/uploads/2018/10/writing-c-program-on-ubuntu-linux-500x281.png 500w, /wp-content/uploads/2018/10/writing-c-program-on-ubuntu-linux-1024x576.png 1024w, /wp-content/uploads/2018/10/writing-c-program-on-ubuntu-linux-982x552.png 982w, /wp-content/uploads/2018/10/writing-c-program-on-ubuntu-linux-400x225.png 400w" sizes="(max-width: 1920px) 100vw, 1920px" />](/wp-content/uploads/2018/10/writing-c-program-on-ubuntu-linux.png)

Now open a terminal and execute the below command

```bash
gcc test.c -o test

```

Here gcc is the tool using which you will compile your C program. `test.c` is the file name of your code (‘.c' is the extention of a C program). `-o` argument is passed to tell the compiler that while making the executable file of my program `test.c`, name it as `test`. You can also use another name other that `test` like `myExecutedFile` or something. Now run your code by executing the command below.

```bash
./test

```

In linux `./` is used to run an executable file. In our case executable file is `test`

[<img loading="lazy" src="/wp-content/uploads/2018/10/running-c-program-on-ubuntu-linux.png" alt="Running C program" width="1920" height="1080" class="aligncenter size-full wp-image-1101" srcset="/wp-content/uploads/2018/10/running-c-program-on-ubuntu-linux.png 1920w, /wp-content/uploads/2018/10/running-c-program-on-ubuntu-linux-500x281.png 500w, /wp-content/uploads/2018/10/running-c-program-on-ubuntu-linux-1024x576.png 1024w, /wp-content/uploads/2018/10/running-c-program-on-ubuntu-linux-982x552.png 982w, /wp-content/uploads/2018/10/running-c-program-on-ubuntu-linux-400x225.png 400w" sizes="(max-width: 1920px) 100vw, 1920px" />](/wp-content/uploads/2018/10/running-c-program-on-ubuntu-linux.png)

### Running a C++ program

Create a text file named `test.cc (you can also use test.cpp)`  
[<img loading="lazy" src="/wp-content/uploads/2018/10/writing-c-plus-plus-program-on-ubuntu-linux.png" alt="Writing C++ program" width="1920" height="1080" class="aligncenter size-full wp-image-1103" srcset="/wp-content/uploads/2018/10/writing-c-plus-plus-program-on-ubuntu-linux.png 1920w, /wp-content/uploads/2018/10/writing-c-plus-plus-program-on-ubuntu-linux-500x281.png 500w, /wp-content/uploads/2018/10/writing-c-plus-plus-program-on-ubuntu-linux-1024x576.png 1024w, /wp-content/uploads/2018/10/writing-c-plus-plus-program-on-ubuntu-linux-982x552.png 982w, /wp-content/uploads/2018/10/writing-c-plus-plus-program-on-ubuntu-linux-400x225.png 400w" sizes="(max-width: 1920px) 100vw, 1920px" />](/wp-content/uploads/2018/10/writing-c-plus-plus-program-on-ubuntu-linux.png)

Now open a terminal and execute the below command

```bash
g++ test.cc -o test
```


Here g++ is the tool using which you will compile your C++ program. `test.cc` is the file name of your code (‘.cc' and .cpp are the extentions of a C++ program). `-o` argument is passed to tell the compiler that while making the executable file of my program `test.cc`, name it as `test`. Now run your code by executing the command below.

```bash
./test
```


[<img loading="lazy" src="/wp-content/uploads/2018/10/running-c-plus-plus-program-on-ubuntu-linux.png" alt="Running C++ program" width="1920" height="1080" class="aligncenter size-full wp-image-1104" srcset="/wp-content/uploads/2018/10/running-c-plus-plus-program-on-ubuntu-linux.png 1920w, /wp-content/uploads/2018/10/running-c-plus-plus-program-on-ubuntu-linux-500x281.png 500w, /wp-content/uploads/2018/10/running-c-plus-plus-program-on-ubuntu-linux-1024x576.png 1024w, /wp-content/uploads/2018/10/running-c-plus-plus-program-on-ubuntu-linux-982x552.png 982w, /wp-content/uploads/2018/10/running-c-plus-plus-program-on-ubuntu-linux-400x225.png 400w" sizes="(max-width: 1920px) 100vw, 1920px" />](/wp-content/uploads/2018/10/running-c-plus-plus-program-on-ubuntu-linux.png)

## Using IDE

Using IDE, running a C or C++ program is very easy and productive. Here we are going to use Geany application. So first install geany by using the command below.

```bash
sudo apt-get install geany
```


Now create a new file test.c in geany.  
Compile using `Build Menu > Compile`  
Build using `Build Menu > Build`  
Execute using `Build Menu > Execute`  
[<img loading="lazy" src="/wp-content/uploads/2018/10/geany-menu-bar.png" alt="Geany menu bar" width="1104" height="563" class="aligncenter size-full wp-image-1108" srcset="/wp-content/uploads/2018/10/geany-menu-bar.png 1104w, /wp-content/uploads/2018/10/geany-menu-bar-500x255.png 500w, /wp-content/uploads/2018/10/geany-menu-bar-1024x522.png 1024w, /wp-content/uploads/2018/10/geany-menu-bar-982x501.png 982w, /wp-content/uploads/2018/10/geany-menu-bar-400x204.png 400w" sizes="(max-width: 1104px) 100vw, 1104px" />](/wp-content/uploads/2018/10/geany-menu-bar.png)

You can also compile, build and execute directly using buttons.  
[<img loading="lazy" src="/wp-content/uploads/2018/10/geany-ide-c-programming.png" alt="Geany IDE C programming" width="1170" height="457" class="aligncenter size-full wp-image-1109" srcset="/wp-content/uploads/2018/10/geany-ide-c-programming.png 1170w, /wp-content/uploads/2018/10/geany-ide-c-programming-500x195.png 500w, /wp-content/uploads/2018/10/geany-ide-c-programming-1024x400.png 1024w, /wp-content/uploads/2018/10/geany-ide-c-programming-982x384.png 982w, /wp-content/uploads/2018/10/geany-ide-c-programming-400x156.png 400w" sizes="(max-width: 1170px) 100vw, 1170px" />](/wp-content/uploads/2018/10/geany-ide-c-programming.png)

You can do the same for C++ programs also.
