---
author: admin
comments: false
date: 2014-10-03 13:26:37+00:00
layout: post
link: https://witr.net/quotation/?p=601
slug: delete-one-of-duplicated-rows-in-table-rownum-with-postgresql
title: delete one of duplicated rows in table (rownum with postgresql)
wordpress_id: 601
categories:
- postgresql
---


You have to delete one of duplicated row within table which doesn't have a primary key:


    
    
    delete from <table> 
     where ctid = (select min(ctid) from <table>);
    




