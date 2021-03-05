---
title: How to create a static site generator
created: 2020-02-28T13:48:11+05:30
author: ashishdoneriya
description: This article will teach you how to create your own static site generator from scratch in any language
permalink: /create-static-site-generator.html
categories:
  - web-development
tags:
  - ssg
  - java
---

In this article I am going to tell you how to create a static site generator. I've created a static site generator in Java. Based on that experience I'll tell you the steps required.

**Reasons why I decided to create my own static site generator -**

**1.** There are a lot of very famous static site generators like Jekyll, Hugo, Hexo, but I always feel disconnected from them because they are written in language that I'm not familier with.
**2.** In every SSG there are always some important features which donot exists. Since I didn't know the language in which they are writting. Therefore I always had to search some third party tools for quick fixing.
**3.** I don't want to do phd in those new frameworks.
**4.** I want to create and customize new themes according to my requirements.

As we already know static site generators are famous because they create static html pages which is very fast. In a SSG (static site generator) we define our website / blog layouts in one directory and posts / pages in another directory. During compilation SSG does the magic and generete all blogs and pages according to their defined layouts.

**The main features in a blog website are -**

**1.** Blog posts
**2.** Categories
**3.** Tags
**4.** Authors
**5.** Pages
**6.** Comments

The SSG we are going to create here should contain all the features above.

**1.** It should generate blogs pages.
**2.** It should be able to display posts according to specific category, tag or author.
**3.** It should be able to generate individual pages also from their content.
**4.** Commenting system is a drawback of SSGs. However there are some alternatives available.

**Things required for creating a SSG -**

**1.** A Programming language
**2.** A Template engine for that programming language
**3.** Markdown parser for that language (if you are writing blog posts in markdown format)
**4.** Programming skills

In Go language there is an integrated template engine in it and Golang is very fast according to reviews, but I'm not so efficient in it.

In my case I was most familier with Java and also very efficient in it. Therefore I decided to code in Java and for template engine I chose Apache Velocity as a template engine for Java. 

Template engine is a very critical component in creating a SSG. Make sure the template engine you selected must contain these features - 

**1.** If condition
**2.** Loop
**3.** Declaring variabled
**4.** Including one template file into the other

For creating SSG first we are going to learn how to create templates (layouts) and after that how to use those layouts and feed data to it.

#### How to create Templates / Layouts / Theme

Lets consider the below page

```html
<html>
	<head>
	<!-- head content -->
	</head>
	<body>
		<div class="someId">
		--your--site-name--
		--categories---
		---page-content---
		<footer>
		<!-- footer content -->
		</footer>
		</div>
	</body>
</html>
```