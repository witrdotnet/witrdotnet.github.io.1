---
author: admin
comments: false
date: 2013-10-17 11:16:00+00:00
layout: post
link: https://witr.net/quotation/?p=17
slug: wireshark-under-ubuntu
title: wireshark under ubuntu
wordpress_id: 17
categories:
- linux
- network
---


1. configure network of cirtual Machine  
in VirtualBox --> settings of virtualMachine(ubuntu) --> Network --> set Promiscuous Mode to allow All  
2. start virtual Machine ubuntu  
3. install wireshark  
> sudo apt-get install wireshark  
4. enable root privilege to dumpcap  
> sudo setcap 'CAP_NET_RAW+eip CAP_NET_ADMIN+eip' /usr/bin/dumpcap  
5. that's all  


  




