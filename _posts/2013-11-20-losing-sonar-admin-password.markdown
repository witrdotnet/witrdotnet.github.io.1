---
author: admin
comments: false
date: 2013-11-20 13:58:00+00:00
layout: post
link: https://witr.net/quotation/?p=685
slug: losing-sonar-admin-password
title: losing sonar admin password
wordpress_id: 685
categories:
- sonar
---

by default sonar creates admin account : user: admin, password : admin  
when sonar admin password is changed and lost, simple way to reinitialize password to admin is with a simple sql command :  
> musql -u sonar -p  
mysql> use sonar  
mysql> update users set crypted_password = '88c991e39bb88b94178123a849606905ebf440f5', salt='6522f3c5007ae910ad690bb1bdbf264a34884c6d' where login = 'admin'  
that’s all.  


  




