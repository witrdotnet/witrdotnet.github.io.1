---
author: admin
comments: false
date: 2013-05-16 07:14:00+00:00
layout: post
link: https://witr.net/quotation/?p=63
slug: tar-exclude
title: tar exclude
wordpress_id: 63
categories:
- linux
---

May 16, 2013  
  
  
pour exclure un dossier du tar créé:  
soit le dossier : /home/fol  
qui contient  
/home/fol/data1/  
et /home/fol/data2/  
et /home/fol/tmp1/  
et /home/fol/tmp2/  
  
on veut faire un tar de "fol" en excluant les dossier "tmp1" et "tmp2":  
cd /home  
tar -czvf fol.tgz fol --exclude 'fol/tmp1' --exclude 'fol/tmp2'  
  
et le tour est joué  
  
  


