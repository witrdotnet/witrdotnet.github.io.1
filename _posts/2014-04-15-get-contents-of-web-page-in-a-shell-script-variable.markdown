---
author: admin
comments: false
date: 2014-04-15 16:37:31+00:00
layout: post
link: https://witr.net/quotation/?p=477
slug: get-contents-of-web-page-in-a-shell-script-variable
title: get contents of web page in a shell script variable
wordpress_id: 477
categories:
- linux
- shell
---


To get contents of web page in a shell script variable we can use wget or curl like following

**WGET**

    
    
    wHome=$(wget witr.net -q -O -)
    echo $wHome
    



**CURL**

    
    
    wHome=$(curl -L witr.net)
    echo $wHome
    




