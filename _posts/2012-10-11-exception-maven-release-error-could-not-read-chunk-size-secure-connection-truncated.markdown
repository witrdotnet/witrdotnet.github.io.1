---
author: admin
comments: false
date: 2012-10-11 07:39:00+00:00
layout: post
link: https://witr.net/quotation/?p=89
slug: exception-maven-release-error-could-not-read-chunk-size-secure-connection-truncated
title: 'exception : maven release error : Could not read chunk Size: secure connection
  truncated'
wordpress_id: 89
categories:
- exception
- maven
---


  
October 11, 2012  
  
Could not read chunk Size: secure connection truncated  
http://adventuresindotnet.blogspot.fr/2010/09/svn-trouble.html  
- svn server 1.6.11  
- eclipse juno + svnkit 1.3.8  
- apache maven 2.2.1  
quand je fait une maven release tout va bien jusqu'au tag de la version. mais après quand il essaye de récupérer le tag avec un "svn checkout" ça montre qu'il récupère les fichiers du svn... mais après un certain temps ça plante avec un message d'erreur svn (could not read chunk size: secure connection truncated). côté serveur apache httpd (message d'erreur : comme dans l'article)  
même problème que dans l'article. j'ai augmenté le timeout sans que cela résout le pb. Solution: changer le client svn : j'ai svn-win32-1.5.6 .j'ai essayé 1.6.6 / 1.6.11 / 1.6.15  (téléchargeables ici http://sourceforge.net/projects/win32svn/files/) et essayer dans une ligne de commande dos "svn checkout --username xxx --password xxx https://svn.xxx.fr/project/tags/xxx" en vain.  
Avec la dernière version du svn client 1.7.6, le svn checkout ça marche. Mais quand j'essaye avec maven release-prepare => erreur : working copy is too old (c'est normal la copie dans svn est format 10 créé avec un svn server 1.6.11) et le client est plus récent 1.7.6.  
enfin j'ai essayé un svn checkout avec le client svn-win32-1.6.19 ça marche. bingo
