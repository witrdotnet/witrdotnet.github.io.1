---
author: admin
comments: false
date: 2014-07-02 08:39:48+00:00
layout: post
link: https://witr.net/quotation/?p=527
slug: remove-all-svn-files-from-checkout-project-directory
title: remove all svn files from checkout project directory
wordpress_id: 527
categories:
- linux
- svn
- tricks
---


Type 

    
    
    find . -name .svn -exec rm -rf {} ;
    



Before check that only ".svn" folders will be deleted

    
    
    find . -name .svn -exec ls {} ;
    




