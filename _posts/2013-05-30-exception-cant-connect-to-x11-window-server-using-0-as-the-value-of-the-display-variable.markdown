---
author: admin
comments: false
date: 2013-05-30 06:58:00+00:00
layout: post
link: https://witr.net/quotation/?p=56
slug: exception-cant-connect-to-x11-window-server-using-0-as-the-value-of-the-display-variable
title: 'exception: Can''t connect to X11 window server using '':0'' as the value of
  the DISPLAY variable'
wordpress_id: 56
categories:
- exception
- linux
---


  
=========================================== 30/05/2013  
If you have following error: Can't connect to X11 window server using ':0' as the value of the DISPLAY variable.  
you must know that :  
- linux user (launching process requsting Xserver) is not authorized to access Xserver  
- OR DISPLAY variable is bad configured  
  
type xhost to know:  
  
> xhost  
No protocol specified  
No protocol specified  
xhost:  unable to open display "???"  
==> means you don't have authorization to any Xserver  
==> to authorize access type: > sudo xhost +SI:localuser:youruser  
  
> xhost  
xhost:  unable to open display "???"  
==> means DISPLAY variable is bad configured  
==> you must fix DISPLAY variable. type: > export DISPLAY=hostname:D.S  
- hostname is the name of the computer where the X server runs. An omitted hostname means the localhost.  
- D is a sequence number (usually 0). It can be varied if there are multiple displays connected to one computer.  
- S is the screen number. A display can actually have multiple screens. Usually there's only one screen though where 0 is the default.  


  




