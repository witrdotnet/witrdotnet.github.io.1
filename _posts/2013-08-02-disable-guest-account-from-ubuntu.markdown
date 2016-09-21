---
author: admin
comments: false
date: 2013-08-02 15:07:00+00:00
layout: post
link: https://witr.net/quotation/?p=21
slug: disable-guest-account-from-ubuntu
title: disable guest account from ubuntu
wordpress_id: 21
categories:
- linux
---

edit lightdm.conf 
    
    sudo vi /etc/lightdm/lightdm.conf


add or edit following property line 
    
    allow-guest=false



