---
author: admin
comments: false
date: 2015-02-18 11:39:33+00:00
layout: post
link: https://witr.net/quotation/?p=704
slug: mount-webdav-directory
title: mount webdav directory
wordpress_id: 704
categories:
- linux
---


- install davfs2


<blockquote>
witr$ sudo apt-get install davfs2
</blockquote>


- create folder


<blockquote>
witr$ sudo mkdir /mnt/wdav
</blockquote>


- mount wbeddav


<blockquote>
witr$ sudo mount.davfs https://webdav.witr.net /mnt/wdav
   Username: witr
   Password: 
</blockquote>



