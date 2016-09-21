---
author: admin
comments: false
date: 2013-07-30 13:01:00+00:00
layout: post
link: https://witr.net/quotation/?p=25
slug: share-folder-from-ubuntu-to-windows
title: share folder from ubuntu to windows
wordpress_id: 25
categories:
- linux
- network
- samba
---


  
We describe here how to share folder in ubuntu within Samba:  




  * host : ubuntu


  * host ip : 10.10.3.52


  
- Edit "smb.conf" 

    
    sudo vi /etc/samba/smb.conf 


- Add following : 

    
    
    [myshared]
    path = /home/witr/myFolder
    available = yes
    valid users = witr
    read only = no
    guest ok = no
    browsable = yes
    public = yes
    writable = yes
    


- Restart samba:

    
    sudo service smbd restart 


- In windows, mount new drive :  
a. choose drive letter,  
b. select network->ubuntu->myshared or type \10.10.3.52myshared  
c. when request user and password, use one of valid users (here witr)
