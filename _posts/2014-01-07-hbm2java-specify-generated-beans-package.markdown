---
author: admin
comments: false
date: 2014-01-07 19:13:57+00:00
layout: post
link: https://witr.net/quotation/?p=696
slug: hbm2java-specify-generated-beans-package
title: 'hbm2java : specify generated beans package'
wordpress_id: 696
categories:
- ant
- hibernate
- java
---


To specify the package of generated java beans in hbm2java ant task, add jdbcconfiguration tag property "packagename" like following :

    
    
    <jdbcconfiguration revengfile="reveng.xml" packagename="net.witr.hbm2java" configurationfile="hibernate.cfg.xml"></jdbcconfiguration>
    



