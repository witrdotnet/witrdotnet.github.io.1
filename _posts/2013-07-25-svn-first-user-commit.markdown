---
author: admin
comments: false
date: 2013-07-25 14:09:00+00:00
layout: post
link: https://witr.net/quotation/?p=27
slug: svn-first-user-commit
title: svn first user commit
wordpress_id: 27
categories:
- java
- svn
---

print users who commits frst commit for each class in project : 

<blockquote>> find -name "*.java" -exec svn log -l1 -r1:HEAD {} ; | grep "|" | awk '{print $3}' </blockquote>

print java class name and user who leaves first commit of that class  
(user /path_to_java_file/java_file.java) : 

<blockquote>> find -name "*.java" | while read line; do user=$(svn log -l1 -r1:HEAD $line | grep "|" | awk '{print $3}'); echo $user $line; done; </blockquote>



