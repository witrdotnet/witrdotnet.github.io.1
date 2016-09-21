---
author: admin
comments: false
date: 2014-01-01 23:48:45+00:00
layout: post
link: https://witr.net/quotation/?p=281
slug: wordpress-changes-dont-take-effect-immediately
title: Wordpress changes don't take effect immediately
wordpress_id: 281
categories:
- php
- tricks
---


Changes made on php files or appearance customization don't take effect immediately, if the wordpress cache plugin is not disabled.

Edit wp-config.php and disable cache :

    
    
    define('WP_CACHE', false); //Added by WP-Cache Manager
    


Cache plugins are very helpfull. Keep cache DISABLED until you are finished any customization work.

