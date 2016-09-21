---
author: admin
comments: false
date: 2014-06-24 16:02:44+00:00
layout: post
link: https://witr.net/quotation/?p=518
slug: remove-m-characters-in-vi
title: remove ^M characters in vi
wordpress_id: 518
categories:
- linux
- tricks
---



To remove all end of line characters (displayed as ^M), in VI type command:
%s/_CTRL-V_ _CTRL-M_//g

command will appear like following in VI :


<blockquote>
:%s/^M//g
</blockquote>





