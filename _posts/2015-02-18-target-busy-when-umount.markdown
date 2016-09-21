---
author: admin
comments: false
date: 2015-02-18 11:58:55+00:00
layout: post
link: https://witr.net/quotation/?p=705
slug: target-busy-when-umount
title: target busy when umount
wordpress_id: 705
categories:
- linux
---


I have mount webdav directory /mnt/wdav ([more](http://quote.witr.net/?p=683)). And, now, I want to umount it.
but i have following error:


<blockquote>
umount: /mnt/wdav: target is busy
(In some cases useful info about processes that
use the device is found by lsof(8) or fuser(1).)
</blockquote>



first step : find out processes using this mount


<blockquote>
witr$ fuser -u /mnt/wdav
/mnt/wdav:        408c(witr)
</blockquote>


second step : identify process


<blockquote>
witr$ ps 408
  PID TTY      STAT   TIME COMMAND
  408 pts/33   Ss     0:00 /opt/appli
</blockquote>


third step : stop process


<blockquote>
witr$ fuser -k /mnt/wdav
</blockquote>


last step : safe umount


<blockquote>
witr$ sudo umount /mnt/wdav
</blockquote>



