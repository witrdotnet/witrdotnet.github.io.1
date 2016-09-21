---
author: admin
comments: false
date: 2013-04-05 12:30:00+00:00
layout: post
link: https://witr.net/quotation/?p=77
slug: have-your-own-cloud-storage-with-owncloud
title: 'have your own cloud storage with : ownCloud'
wordpress_id: 77
categories:
- apache
- cloud
- owncloud
---

I describe here how to install and confugure your own cloud with owncloud.org  
  
assuming we have apache and mysql intalled   


<blockquote>> wget http://download.owncloud.org/community/owncloud-5.0.13.tar.bz2  
> tar -xjf owncloud-5.0.13.tar.bz2 -C [/path/to/apache]/www/  
> cd /path/to/apache/www/owncloud </blockquote>

and suppose that apache user is www-data and its group is www-data   


<blockquote>> chown -R www-data:www-data [/path/to/your/owncloud]/config  
> chown -R www-data:www-data [/path/to/your/owncloud]/apps  
> mkdir [/path/to/your/owncloud]/data  
> chown -R www-data:www-data [/path/to/your/owncloud]/data </blockquote>

edit /etc/apache2/sites-enabled/000-default and set AllowOverride to All in the Directory /path/to/apache/www/   


<blockquote>> a2enmod rewrite  
> a2enmod headers  
> service apache2 restart </blockquote>

open browser localhost/owncloud and see if some php modules are missed  
- PHP-GD module is required   


<blockquote>> sudo apt-get install php5-gd </blockquote>

- xml parser is required  


<blockquote>> apt-get install php-xml-parser </blockquote>

- no database driver is installed (PHP modules have been installed, but they are still listed as missing)  


<blockquote>> apt-get install php5-mysql (or any other database driver) </blockquote>

restart apache   


<blockquote>> service apache2 restart </blockquote>

and got to http://localhost/owncloud : step require database connection parameters  
create empty mysql database for owncloud   


<blockquote>> mysql -uroot -p  
mysql> use mysql;  
mysql> create user sonar identified by 'sonar';  
mysql> update user set host='%' where user = 'sonar';  
mysql> create database sonar;  
mysql> grant all privileges on sonar.* to sonar;  
mysql> flush privileges;  
mysql> quit </blockquote>

provide database username, password, and dbname to owncloud assistant in http://localhost/owncloud. And let owncloud initializes its database.  
  
now, you have your own cloud !
