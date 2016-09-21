---
author: admin
comments: false
date: 2014-10-03 15:31:53+00:00
layout: post
link: https://witr.net/quotation/?p=603
slug: upgrade-mongodb-under-ubuntu
title: upgrade mongodb under ubuntu
wordpress_id: 603
categories:
- mongodb
---



To upgrade mongodb follow steps bellow :

    
    
    
    $[/home/witr] sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
    
    $[/home/witr] echo 'deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen' | sudo tee /etc/apt/sources.list.d/mongodb.list
    
    $[/home/witr] sudo apt-get update
    
    $[/home/witr] sudo apt-get install mongodb-10gen
    
    



**Note**
While upgrading you have dpkg-deb error processing at step 4
/var/cache/apt/archives/mongodb-10gen_2.4.11_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

You must remove mongodb-clients before apt-get install :

    
    
    
    $[/home/witr] sudo apt-get remove mongodb-clients
    
    $[/home/witr] sudo apt-get install mongodb-10gen
    
    




