---
author: admin
comments: false
date: 2013-04-18 07:21:00+00:00
layout: post
link: https://witr.net/quotation/?p=69
slug: mount-cifs-windows-drive-under-ubuntu
title: mount cifs windows drive under ubuntu
wordpress_id: 69
categories:
- linux
---

April 18, 2013  
  
  
monter un drive cifs windows:  
> mount -t cifs -o rw,username=mba,password=xxxxxx //drive/users /drive/U  
j'ai eu ce message d'erreur  
mount : mauvais type de système de fichiers, option erronée, superbloc  
        erroné sur //drive/users, page de code ou aide manquante, ou autre erreur  
       (pour plusieurs syst. de fichiers (nfs, cifs) vous pouvez avoir  
       besoin d'un programme /sbin/mount. intermédiaire)  
       Dans quelques cas certaines informations sont utiles dans syslog - essayez  
       dmesg | tail  ou quelque chose du genre  
  
  
j'ai regardé dans dmesg  
> dmesg | tail  
j'ai eu:  
[75756.500633] CIFS VFS: cifs_mount failed w/return code = -22  
  
il suffit d'installer cifs-utils pour que le problème soit réglé  
> sudo apt-get install cifs-utils
