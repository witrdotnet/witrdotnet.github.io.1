---
author: admin
comments: false
date: 2015-03-25 10:25:04+00:00
layout: post
link: https://witr.net/quotation/?p=708
slug: save-received-traffic-on-tcp-port-while-the-port-is-in-use
title: save received traffic on tcp port while the port is in use
wordpress_id: 708
categories:
- linux
- network
---


You have to save all received traffic on a tcp port. But there was one process which already listen to that port.

=> use tcpdump : 

    
    
    sudo tcpdump -vv -x -X  -i <interface> 'port <port>' -w <output_file>
    



More pretty and analysable with Wireshark, 
=> use dumpcap : 

    
    
    dumpcap -n -i <interface> -f "port <port>" -w <output_file>
    




