---
author: admin
comments: false
date: 2014-01-07 18:43:14+00:00
layout: post
link: https://witr.net/quotation/?p=694
slug: hbm2java-hibernate-annotations-missed
title: 'hbm2java : hibernate annotations missed'
wordpress_id: 694
categories:
- ant
- hibernate
- java
---


If the build.xml used to generate hibernate beans from DB produces POJO beans without annotations, then add hbm2java tag property "ejb3" :

    
    
       ...
       <hbm2java ejb3="true"></hbm2java>
       ...
    



