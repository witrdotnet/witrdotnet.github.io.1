---
author: admin
comments: false
date: 2014-10-04 06:27:23+00:00
layout: post
link: https://witr.net/quotation/?p=664
slug: clean-system-tablespace
title: clean system data (oracle database)
wordpress_id: 664
categories:
- oracle
---


Following, a useful sql request listing system tables sizes in descending order. It helps to detect which table data could be purged to save more disk space :

    
    
    select owner, segment_name, segment_type, bytes / 1024 / 1024 "size"
      from dba_segments
     where tablespace_name = 'SYSTEM'
     order by "size" desc;
    



Audit table SYS.AUD$ could be the cause of full disk space. Administrator must control the growth and size of the audit trail.


