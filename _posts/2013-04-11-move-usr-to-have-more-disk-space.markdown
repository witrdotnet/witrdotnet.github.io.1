---
author: admin
comments: false
date: 2013-04-11 07:24:00+00:00
layout: post
link: https://witr.net/quotation/?p=72
slug: move-usr-to-have-more-disk-space
title: move /usr to have more disk space
wordpress_id: 72
categories:
- linux
---


  
April 11, 2013  
  
soit votre vm "ubuntu"  
- sudo gparted  
- deux possibilités:  
  1- créer une partiotion ext4 s'il y a un espace non partitionné sur le disque  
  2- démonter la partition qu'on va redimensionner + redimensionner + créer sur la nouvelle partie non partitionné une partition ext4  
- sudo mkdir /media/myusr  
- sudo mount /dev/sdax /mnt/myusr  
- sudo blkid  
............  
/dev/sdax: UUID="xxxx-xxx-xxx"  
..............  
- ajouter cette ligne dans /etc/fstab :  
UUID=xxxx-xxx-xxx /media/myusr ext4 errors=remount-ro  0     1  
- sudo cp -a /usr/. /media/myusr/  
  
arrêter ubuntu.  
crééer une nouvelle vm "tmp" avec un nouveau disk virtuel + y attacher le disk de la vm ubuntu  
et démarrer la nouvelle vm tmp  
- sudo blkid  
............  
/dev/sdax: UUID="yyyy-yyy-yyy"  
..............  
/dev/sdbx: UUID="xxxx-xxx-xxx"  
..............  
- mkdir /dev/sdbx /media/sdbroot  
où sdbx est la partition boot de ubuntu qui contient /usr  
- sudo mount /dev/sbdx /media/sdbroot  
- sudo rm -rf /media/sdbroot/usr/*  
- vi /media/sdbroot/etc/fstab  
- modifier cette ligne dans /etc/fstab :  
UUID=xxxx-xxx-xxx /media/myusr ext4 errors=remount-ro  0     1  
remplacer /media/myusr par /usr  
UUID=xxxx-xxx-xxx /usr ext4 errors=remount-ro  0     1  
- sudo umount /dev/sbdx  
- arrêter la vm tmp + supprimer là si vous voules (on en a plus besoin)  
- démarrer la vm ubuntu et le /usr est bine déplacé sur la nouvelle partition !  
  


