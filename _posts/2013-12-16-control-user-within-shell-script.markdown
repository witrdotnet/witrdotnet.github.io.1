---
author: admin
comments: false
date: 2013-12-16 15:55:26+00:00
layout: post
link: https://witr.net/quotation/?p=110
slug: control-user-within-shell-script
title: control user within shell script
wordpress_id: 110
categories:
- linux
- shell
---

If our script must be launched with witr user :

    
    if [ $USER != witr ] ; then   echo "must connect as witr" ; exit ; fi



