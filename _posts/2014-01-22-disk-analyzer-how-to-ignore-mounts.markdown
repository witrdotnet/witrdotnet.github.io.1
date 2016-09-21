---
author: admin
comments: false
date: 2014-01-22 09:11:42+00:00
layout: post
link: https://witr.net/quotation/?p=700
slug: disk-analyzer-how-to-ignore-mounts
title: 'disk analyzer : how to ignore mounts'
wordpress_id: 700
categories:
- linux
- tricks
---


under ubuntu the default disk analyser (baobab) don't offer ignore directories option.
In the case of we would like analyse the root folder / and ignore mounts in /media for example the easy way is to : 
- create new temporary folder, 
- mount the root filesystem on it, 
- analyse the temporary folder
- unmount and delete it

So, first proceed like following


<blockquote>
> sudo mkdir tmpAnalysis
> sudo mount /dev/sda1 tmpAnalysis
> baobab tmpAnalysis
</blockquote>


Analysis is ready to explore.
Then 


<blockquote>
> sudo umount tmpAnalysis
> sudo rm -rf tmpAnalysis
</blockquote>



