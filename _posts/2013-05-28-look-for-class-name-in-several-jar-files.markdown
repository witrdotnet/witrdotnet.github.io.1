---
author: admin
comments: false
date: 2013-05-28 06:56:00+00:00
layout: post
link: https://witr.net/quotation/?p=60
slug: look-for-class-name-in-several-jar-files
title: look for class name in several jar files
wordpress_id: 60
categories:
- java
- linux
---


  
=========================================== 28/05/2013  
look for class name in several jar files:  
ll path-to-jars/ | awk {'print "path-to-jars/"$9'} | grep ".jar" | while read thejar; do echo $thejar; jar -tvf $thejar | grep "yourClassName pattern"; done  
previous command line will echo each jar file name and then classes that names matches your pattern  


  




