---
author: admin
comments: false
date: 2014-05-27 10:50:09+00:00
layout: post
link: https://witr.net/quotation/?p=510
slug: recover-lost-centos-56-root-password
title: recover lost centos 5&6 root password
wordpress_id: 510
categories:
- linux
- system
- tricks
---


1. Reboot
2. Press any key after reboot when boot countdown, to go to GRUB menu
3. From that menu, select the appropriate kernel version and press the 'e' key
4. Then select the kernel /vmlinuz-... line and press the 'e' key 
5. At the end of displayed line type space and then type 1 (you can type 's' or 'single' rather than '1'). Press Enter to save changes
6. You should already be on the kernel /vmlinuz... line. Press the 'b' key to boot to these temporary options to allow you to recover your root password
7. When prompted type 'passwd' and press enter. You will be prompted to type new password twice
8. After typing new password and confirming it, type 'reboot' command.

Got from [here](http://community.spiceworks.com/how_to/show/4022-reset-root-password-on-centos-5-6)

