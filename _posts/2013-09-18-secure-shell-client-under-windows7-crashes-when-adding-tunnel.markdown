---
author: admin
comments: false
date: 2013-09-18 11:21:00+00:00
layout: post
link: https://witr.net/quotation/?p=20
slug: secure-shell-client-under-windows7-crashes-when-adding-tunnel
title: Secure Shell Client under Windows7 crashes when adding tunnel
wordpress_id: 20
categories:
- ssh
---

With the gui of Secure Shell client under windows7, when you try to add outgoing tunnel it crashes and windows tell you that program will be ended.  
  
Solution :  
1. create an incoming tunnel with your ssh profile :  
    Menu profiles --> edit profiles  
    Then choose "Tunneling" tab and finally choose "Incoming" tab  
    Save  
2. go to C:UserswitrApplication DataSSH and edit your profile XXX.ssh2 with simple text editor  
you must find your declared incoming tunnel like so :

    
    
    ....
    [Outgoing Tunnels]
    
    [Incoming Tunnels]
    Tunnel=S:witrTunnel,1521,localhost,1521,0,tcp
    ....
    


3. move declared incoming tunnel to outgoing tunnels section and save  
4. reconnect with Secure Shell Client and now must be go.
