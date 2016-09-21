---
author: admin
comments: false
date: 2015-03-25 10:34:46+00:00
layout: post
link: https://witr.net/quotation/?p=710
slug: extract-json-text
title: extract json text
wordpress_id: 710
categories:
- json
- linux
---



    
    
    
    cat <file> | while read line ; do echo -e `expr match "$line" '\({.*}\)'`; done | grep "{"
    
    



