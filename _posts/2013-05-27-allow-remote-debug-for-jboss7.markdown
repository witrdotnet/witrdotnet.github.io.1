---
author: admin
comments: false
date: 2013-05-27 06:55:00+00:00
layout: post
link: https://witr.net/quotation/?p=61
slug: allow-remote-debug-for-jboss7
title: allow remote debug for jboss7
wordpress_id: 61
categories:
- jboss
---


  
=========================================== 27/05/2013  
allow remote debug for jboss7  
(https://community.jboss.org/thread/175385)  
1. Check the standalone.conf (or standalone.conf.bat for Windows OS) and uncomment the following line:  
#JAVA_OPTS="$JAVA_OPTS -Xrunjdwp:transport=dt_socket,address=8787,server=y,suspend=n"  


  




