---
author: admin
comments: false
date: 2013-03-19 08:34:00+00:00
layout: post
link: https://witr.net/quotation/?p=84
slug: wireshark-and-npf-under-windows7
title: wireshark and npf under windows7
wordpress_id: 84
categories:
- network
---


  
March 19, 2013  
  
wireshark can not start capture because npf is not running under windows7.  
solution : execute cmd.exe as administrator and type:  
> sc qc npf  
this will display th state of npf. if it's not running then type  
> sc start npf  
if you want to set auto start type  
> sc config npf start=auto  


  




