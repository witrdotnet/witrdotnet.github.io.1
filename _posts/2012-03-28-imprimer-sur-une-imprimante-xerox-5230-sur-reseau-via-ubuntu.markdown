---
author: admin
comments: false
date: 2012-03-28 07:44:00+00:00
layout: post
link: https://witr.net/quotation/?p=97
slug: imprimer-sur-une-imprimante-xerox-5230-sur-reseau-via-ubuntu
title: imprimer sur une imprimante Xerox 5230 sur réseau via ubuntu
wordpress_id: 97
categories:
- linux
---

March 28, 2012  
  
imprimer sur une imprimante Xerox 5230 sur réseau via ubuntu :  
  
1) vi /etc/cups/ppd/.ppd   
2) change the line : *cupsFilter: "application/vnd.cups-postscript 0 /Library/Printers/Xerox/filter/XeroxPSFilter" to *%*cupsFilter: "application/vnd.cups-postscript 0 /Library/Printers/Xerox/filter/XeroxPSFilter"  
3) sudo service cups restart ==> ubuntuforums.org/showthread.php?t=1576382
