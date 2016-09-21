---
author: admin
comments: false
date: 2013-01-16 09:36:00+00:00
layout: post
link: https://witr.net/quotation/?p=87
slug: vbox-resize-partition
title: vbox resize partition
wordpress_id: 87
categories:
- linux
---

January 16, 2013  
  
  
1- create new vdi with wanted size  
2- copy old vdi in new (dos command): VBoxManage.exe clonehd c:...old.vdi c:...new.vdi --existing  
3- link new vdi to you vm and restart your vm  
4- in your vm terminal transform free space on partition with gparted utils : sudo gparted  
5- if created partition is /dev/sda3, then mount it in any folder you want. mnt for example : sudo mount /dev/sda3 /mnt
