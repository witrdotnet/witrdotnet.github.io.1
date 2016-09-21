---
author: admin
comments: false
date: 2013-12-05 16:43:00+00:00
layout: post
link: https://witr.net/quotation/?p=691
slug: get-last-10-log-of-several-svn-projects
title: get last 10 log of several svn projects
wordpress_id: 691
categories:
- shell
- svn
---

We have 10 projects checked out from svn repo:  
/workspace/proj1  
/workspace/proj2  
/workspace/proj3  
... etc  
  
get last 10 log of several svn projects with shell comand line :
    
    ls -1 | while read proj; do echo "============$proj"; svn log -l 10 $proj; done



