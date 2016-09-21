---
author: admin
comments: false
date: 2012-03-29 07:43:00+00:00
layout: post
link: https://witr.net/quotation/?p=94
slug: oublier-le-mot-de-passe-root-mysql-ubuntu
title: oublier le mot de passe root mysql ubuntu
wordpress_id: 94
categories:
- mysql
---

March 29, 2012  
  
oublier le mot de passe root mysql ubuntu:  
  
1) sudo service mysql stop  
2) sudo mysqld_safe --skip-grant-tables  
3) dans un autre terminal : mysql -u root mysql  
4) update user set Password=PASSWORD('newPassword') where user='root';  
4) flush privileges;  
5) exit;  
6) c'est tout source: http://www.howtoforge.com/reset-forgotten-mysql-root-password
