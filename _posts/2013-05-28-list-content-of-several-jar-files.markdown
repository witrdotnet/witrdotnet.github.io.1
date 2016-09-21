---
author: admin
comments: false
date: 2013-05-28 06:56:00+00:00
layout: post
link: https://witr.net/quotation/?p=59
slug: list-content-of-several-jar-files
title: list content of several jar files
wordpress_id: 59
categories:
- java
- linux
---


  
=========================================== 28/05/2013  
list content of several jar files:  
ll path-to-jars/ | awk {'print "path-to-jars"$9'} | grep ".jar" | xargs -n 1 jar -tvf  


  




