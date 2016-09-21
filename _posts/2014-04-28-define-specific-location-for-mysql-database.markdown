---
author: admin
comments: false
date: 2014-04-28 15:34:54+00:00
layout: post
link: https://witr.net/quotation/?p=703
slug: define-specific-location-for-mysql-database
title: define specific location for mysql database
wordpress_id: 703
categories:
- mysql
---


You can define different database location with simple symlink 
**create new database witrDB**


<blockquote>
$ mysql -u witr -p
  > CREATE DATABASE witrDB;
  > quit
</blockquote>


**list all stored databases**


<blockquote>
$ sudo ls /var/lib/mysql/
</blockquote>


witrDB must be listed
**stop mysql service**


<blockquote>
$ sudo service mysql stop
</blockquote>


**move witrDB to different location**


<blockquote>
$ sudo mv /var/lib/mysql/witrDB /drive/myDrive/myDatabases/
</blockquote>


**create symlink**


<blockquote>
$ sudo ln -s /drive/myDrive/myDatabases/witrDB /var/lib/mysql/witrDB
</blockquote>


**restart mysql service**


<blockquote>
$ sudo service mysql start
</blockquote>



If mysql server jobs start fails: 
1. ensure that linux user have rights on your new database directory


<blockquote>
$ chown youruser.yourgroup /drive/myDrive/myDatabases/witrDB
</blockquote>


2. look for apparmor config


<blockquote>
$ sudo vi /etc/apparmor.d/usr.sbin.mysqld
</blockquote>


add these two lines:
  /mnt/perso/mysql.perso/ r,
  /mnt/perso/mysql.perso/** rwk,


<blockquote>
 $ sudo service apparmor restart
</blockquote>


3. restart mysql service and try again


<blockquote>
$ sudo service mysql restart
</blockquote>



