---
author: admin
comments: false
date: 2014-04-22 11:23:11+00:00
layout: post
link: https://witr.net/quotation/?p=701
slug: delete-duplicate-lines-within-text-file
title: delete duplicate lines within text file
wordpress_id: 701
categories:
- linux
- tricks
---


Delete duplicate lines within a text file in two steps:
- sort file : sort command
- extract lines and ignore duplicate ones : awk '!x[$0]++'



<blockquote>
> sort input.txt | awk '!x[$0]++' >> output.txt
</blockquote>




