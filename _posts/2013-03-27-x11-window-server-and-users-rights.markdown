---
author: admin
comments: false
date: 2013-03-27 08:29:00+00:00
layout: post
link: https://witr.net/quotation/?p=78
slug: x11-window-server-and-users-rights
title: x11 window server and users rights
wordpress_id: 78
categories:
- exception
- linux
---

March 27, 2013  
  
  
if you get exception similar to the following: Can't connect to X11 window server  
  
check your DISPLAY env variable : > echo $DISPLAY  
fix it if not correct : > export DISPLAY=:0  
  
if it's correctly set but you have the problem. May your linux user you have using don't have rights to the xhost.  
check this closure by typing: > xhost  
  
if your user is not in the list, give it the right to connect to the X11 window server by typing: > xhost +SI:localuser:jboss
