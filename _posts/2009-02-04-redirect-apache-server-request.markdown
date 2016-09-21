---
author: admin
comments: false
date: 2009-02-04 17:27:00+00:00
layout: post
link: https://witr.net/quotation/?p=103
slug: redirect-apache-server-request
title: redirect apache server request
wordpress_id: 103
categories:
- apache
---

In httpd.conf add the following  


<blockquote>  
   ServerName mba  
   Redirect / http://10.1.3.17:9080/  
</blockquote>




Then restart apache : service apache2 restart



